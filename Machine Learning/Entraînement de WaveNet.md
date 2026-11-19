#ml-2

# Modèle

L'[[Architecture WaveNet|architecture WaveNet]] s'entraîne de façon supervisée comme un modèle autorégressif : le réseau reçoit une séquence d'échantillons audio et produit, pour chaque position, une distribution sur l'échantillon suivant, comparée à la séquence audio cible. L'objectif est la densité jointe de la séquence, factorisée en probabilités conditionnelles :

$$p(\mathbf{x}) = \prod_{t=1}^{n} p(x_t \mid x_1, \dots, x_{t-1})$$

Le [[Champ récepteur d'une pile de convolutions|champ récepteur]] $R$ limite le contexte réellement lu par chaque sortie aux $R$ échantillons précédents :

$$\hat{\mathbf{p}}_t = f(x_{t-R}, \dots, x_{t-1})$$

Pour $R=4$, la sortie en position $t$ s'écrit $f(x_{t-4}, x_{t-3}, x_{t-2}, x_{t-1})$. Chaque échantillon est un code pris parmi les $256$ valeurs de la [[Compression mu-law]] : la fonction $f$ renvoie un vecteur de probabilités $\hat{\mathbf{p}}_t \in \mathbb{R}^{256}$ et la [[Entropie croisée multi-classe|perte d'entropie croisée]] de cette position s'écrit

$$\ell_t = \mathcal{L}(\hat{\mathbf{p}}_t, x_t) = -\log \hat{p}_{t,\,x_t}$$

$\mathcal{L}$ désigne la perte d'une position ; la perte moyenne sur toute la séquence est notée $\bar{\mathcal{L}}$.

Chaque position de la séquence constitue un exemple d'entraînement : une fenêtre de $R$ échantillons en entrée, l'échantillon suivant en cible. La sortie en position $t$ est évaluée contre l'échantillon audio $t$, jamais contre un autre.

# Propriétés

La perte moyenne porte sur les positions où la prédiction est possible, de $t=R+1$ à $t=n$ :

$$\bar{\mathcal{L}} = \frac{1}{n-R}\sum_{t=R+1}^{n}\ell_t = \frac{1}{12-4}\sum_{t=5}^{12}\ell_t$$

Pour $n=12$ et $R=4$, les longueurs s'en déduisent :

- entrée : $n-1=11$ échantillons, indices $1$ à $11$ ;
- sortie : $n-R=8$ prédictions, indices $5$ à $12$ ;
- audio cible : $n=12$ échantillons, indices $1$ à $12$ ;
- les $R=4$ premiers échantillons ne sont pas prédictibles, faute de fenêtre complète.

Les $n-R=8$ prédictions d'une séquence sont obtenues en une seule passe avant : le contexte de chaque position est un extrait du signal observé (enseignant forcé), et non la sortie du modèle au pas précédent. Un même signal de longueur $n$ fournit donc $n-R$ exemples simultanés.

# Exemple

Avec $R=4$ et $n=12$, les trois séquences s'alignent colonne par colonne, chaque sortie sous l'échantillon audio qu'elle prédit :

| Position | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Entrée | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | |
| Sortie | | | | | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
| Audio | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |

Les quatre premiers échantillons audio forment le champ récepteur de la première prédiction : la sortie $5$ s'appuie sur les entrées $1, 2, 3, 4$ et se compare à l'échantillon audio $5$, avec la perte $\ell_5$. De proche en proche, la sortie $8$ s'appuie sur les entrées $4, 5, 6, 7$, la sortie $12$ sur les entrées $8, 9, 10, 11$. La perte moyenne de cette séquence vaut

$$\bar{\mathcal{L}} = \frac{1}{8}\left(\ell_5 + \ell_6 + \ell_7 + \ell_8 + \ell_9 + \ell_{10} + \ell_{11} + \ell_{12}\right)$$

Un signal de $12$ échantillons contient $n-R+1=9$ fenêtres de $4$ échantillons, mais la dernière se termine sur l'échantillon $12$ et n'a pas de suivant à prédire : il reste $n-R=8$ paires (fenêtre, cible), donc $8$ cases de sortie, une par échantillon cible effectivement prédit.

# Algorithme

```
x      = audio[:, :, :-1]                 # échantillons 1 à n-1        [B, 1, n-1]
logits = wavenet(x)                       # prédictions de R+1 à n      [B, 256, n-R]
target = mu_law(audio[:, 0, R:])          # échantillons R+1 à n        [B, n-R]
loss   = F.cross_entropy(logits, target)  # 256 classes, codes mu-law
```

L'entrée est le signal privé de son dernier échantillon, la cible est le signal privé de ses $R$ premiers : l'entrée compte $n-1$ positions, tandis que les prédictions et la cible en comptent $n-R$ et se correspondent position par position. Avec un remplissage causal à gauche seulement, la sortie en position $t$ prédit l'échantillon $t+1$ et la cible devient `audio[..., 1:]`.

# Remarque

L'alignement est le point sensible de l'entraînement. Si la cible est décalée d'un pas trop tôt, le modèle voit l'échantillon qu'il doit prédire et apprend à recopier son entrée : la perte d'entraînement tombe presque à zéro, mais la génération ne produit que du bruit. Décalée d'un pas trop tard, la cible fait apprendre deux pas d'avance. Le contrôle pratique consiste à modifier $x_t$ et à vérifier qu'aucune prédiction d'un échantillon d'indice inférieur ou égal à $t$ ne change.

Le nombre de cases de la ligne de sortie vaut $n-R$, une par échantillon cible réellement prédit. Compter $n-R+1$ cases reviendrait à inclure une position sans échantillon suivant à prédire, et compter une case par case d'entrée décale toute la ligne de sortie d'un cran vers la gauche, jusqu'à déborder la colonne $n$.

Les $R$ entrées qui alimentent la sortie $t$ sont $x_{t-R}$ à $x_{t-1}$, et la sortie est placée sous l'échantillon audio $t$ : pour la sortie $8$, la fenêtre est $4, 5, 6, 7$. Une fenêtre postérieure inclurait l'échantillon à prédire, ce qui briserait la causalité et rendrait la génération inutilisable.

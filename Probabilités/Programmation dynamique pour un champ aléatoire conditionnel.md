#adm-8

# Algorithme

La **programmation dynamique pour un champ aléatoire conditionnel** à chaîne linéaire calcule la suite d'étiquettes de score maximal sans énumérer les $K^n$ suites possibles, quand $K$ est le nombre d'étiquettes et $n$ la longueur de la séquence. Elle adapte l'[[Algorithme de Viterbi]] aux scores locaux du champ : au lieu d'enchaîner des probabilités de transition et d'émission, elle additionne les scores $g_s(y_{s-1}, y_s)$ portés par chaque couple d'étiquettes consécutives.

Soit $H(k, v)$ le score de la meilleure séquence d'étiquettes $y_1, \dots, y_k$ dont la dernière étiquette, à la position $k$, vaut $v$ :

$$H(k, v) = \max_{y_1, \dots, y_{k-1}} \left( \sum_{s=1}^{k-1} g_s(y_{s-1}, y_s) + g_k(y_{k-1}, v) \right)$$

Le maximum se décompose en deux étages : choisir l'étiquette $u = y_{k-1}$ de la position précédente, puis, ce choix fait, choisir au mieux les étiquettes plus anciennes. Le maximum intérieur sur $y_1, \dots, y_{k-2}$ n'est autre que $H(k-1, u)$. D'où la récursion

$$H(k, v) = \max_{u} \left( H(k-1, u) + g_k(u, v) \right)$$

Le calcul se conduit de la première position vers la dernière, en remplissant un tableau $H$ indexé par la position et l'étiquette :

```
pour chaque étiquette v :
    H(1, v) = g₁(y₀, v)
pour k de 2 à n :
    pour chaque étiquette v :
        H(k, v) = max sur u de (H(k-1, u) + gₖ(u, v))
        mémoriser l'étiquette u qui réalise ce maximum
choisir l'étiquette v qui maximise H(n, ·)
remonter les prédécesseurs mémorisés pour restituer la séquence
```

# Interprétation

Chaque case du tableau condense un ensemble de chemins : tous ceux qui aboutissent à la même étiquette à la même position, dont seul le meilleur score est conservé. Le maximum étant pris case par case, le nombre de chemins retenus reste de l'ordre du nombre de cases, alors que le nombre de chemins complets croît exponentiellement avec la longueur de la séquence.

La mise en œuvre pratique s'appuie sur la matrice $K \times K$ qui rassemble les valeurs $g_s(y_{s-1}, y_s)$ pour tous les couples d'étiquettes. Une ligne fixe l'étiquette $u$ de la position $s-1$, une colonne l'étiquette $v$ de la position $s$, et la case d'intersection porte le score du couple :

| étiquette $u$ en $s-1$ / étiquette $v$ en $s$ | N | V | ART |
|---|---|---|---|
| N | $g_s(\mathrm{N}, \mathrm{N})$ | $g_s(\mathrm{N}, \mathrm{V})$ | $g_s(\mathrm{N}, \mathrm{ART})$ |
| V | $g_s(\mathrm{V}, \mathrm{N})$ | $g_s(\mathrm{V}, \mathrm{V})$ | $g_s(\mathrm{V}, \mathrm{ART})$ |
| ART | $g_s(\mathrm{ART}, \mathrm{N})$ | $g_s(\mathrm{ART}, \mathrm{V})$ | $g_s(\mathrm{ART}, \mathrm{ART})$ |

Toutes les cases sont renseignées : la matrice est pleine, car aucun couple d'étiquettes n'est a priori interdit. Vue comme un graphe, elle décrit un graphe biparti complet entre les étiquettes de la position $s-1$ et celles de la position $s$, chaque arête portant le score du couple qu'elle relie. Le parcours de proche en proche suit donc une structure de [[Treillis|treillis]], une colonne par position et une ligne par étiquette.

# Remarque

- Le schéma est celui de l'[[Algorithme de Viterbi]], à ceci près que Viterbi combine des probabilités, donc des sommes de logarithmes, tandis que les scores $g_s$ sont déjà additifs : la récursion est la même, un maximum de sommes remplaçant un maximum de produits.
- La validité de la récursion repose sur le [[Principe d'optimalité de Bellman]] : le meilleur chemin aboutissant à la case $(k, v)$ se prolonge un meilleur chemin aboutissant à une case $(k-1, u)$, si bien qu'écarter les autres prédécesseurs ne fait perdre aucune solution optimale.
- Seul le score maximal est obtenu par la récursion ; restituer la séquence elle-même demande de mémoriser, en chaque case, l'étiquette $u$ qui réalise le maximum, puis de remonter ces prédécesseurs depuis la dernière position.
- Le tableau $H$ compte $n$ positions de $K$ cases, chaque case comparant $K$ prédécesseurs : le coût du calcul est de l'ordre de $n K^2$, linéaire en la longueur de la séquence et quadratique en le nombre d'étiquettes.
- Le décodage qui précède ce calcul est décrit dans [[Décodage d'un champ aléatoire conditionnel à chaîne linéaire]] ; les scores $g_s$ y proviennent de la [[Décomposition positionnelle des fonctions de traits]] du [[Champ aléatoire conditionnel à chaîne linéaire]].
- La même récursion décode un [[Champ aléatoire conditionnel sur un réseau de neurones récurrent]], où les scores locaux $A(y_{k-1}, y_k) + \mathbb{P}(k, x, y_k)$ remplacent les combinaisons de fonctions de traits.

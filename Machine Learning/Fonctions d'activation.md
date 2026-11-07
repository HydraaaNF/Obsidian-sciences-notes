#ml-1

# Définition

Une fonction d'activation transforme le score $z$ produit par un [[Neurone artificiel]], c'est-à-dire la somme pondérée de ses entrées augmentée de son biais. Trois fonctions sont d'usage courant.

Sigmoïde :

$$\sigma(z) = \frac{1}{1 + e^{-z}}$$

à valeurs dans $(0, 1)$.

Tangente hyperbolique :

$$\tanh(z) = 2\sigma(2z) - 1$$

à valeurs dans $(-1, 1)$.

ReLU :

$$\mathrm{ReLU}(z) = \max(0, z)$$

à valeurs dans $[0, +\infty)$.

# Propriétés

- La sigmoïde est plate aux deux extrémités et sa dérivée est majorée : $\sigma'(z) \le 0.25$ pour tout $z$.
- La tangente hyperbolique est centrée sur $0$ et présente elle aussi des extrémités plates.
- ReLU a une pente de $1$ pour $z > 0$ et reste peu coûteuse à calculer.

```chart
type: line
labels: ["-3", "-2", "-1", "0", "1", "2", "3"]
series:
  - title: Sigmoïde
    data: [0.05, 0.12, 0.27, 0.5, 0.73, 0.88, 0.95]
  - title: Tanh
    data: [-0.995, -0.964, -0.762, 0.0, 0.762, 0.964, 0.995]
  - title: ReLU
    data: [0.0, 0.0, 0.0, 0.0, 1.0, 2.0, 3.0]
```

Les deux fonctions de type sigmoïde s'aplatissent loin de zéro, tandis que ReLU reste une droite de pente $1$ sur tout le demi-axe positif.

# Interprétation

Le choix de la fonction dépend de la couche et de ce que l'on veut représenter.

- Pour les couches cachées d'un [[Perceptron multicouche]], ReLU est le choix par défaut.
- La sigmoïde, à valeurs dans $(0, 1)$, se lit comme un cadran : elle dose une quantité entre « rien » et « tout ».
- La tangente hyperbolique, à valeurs dans $(-1, 1)$, fournit une valeur signée et bornée.

Un neurone dont l'activation est la sigmoïde calcule exactement une [[Régression logistique]] : toute valeur réelle du score est ramenée dans $(0, 1)$.

# Exemple

Dans une cellule [[Mémoire à long et court terme|LSTM]], les portes utilisent ces deux fonctions.

- $\tilde{c}_t$ (contenu candidat) est calculé par une tangente hyperbolique : une valeur signée et bornée, qui indique ce qui pourrait être écrit.
- $i_t$ (porte d'entrée), $f_t$ (porte d'oubli) et $o_t$ (porte de sortie) sont calculées par des sigmoïdes, qui servent de cadrans : elles mesurent chacune combien d'un contenu écrire, conserver ou montrer dans $h_t$.

Sur une dimension de la mémoire $c$, le sujet est singulier ($+1$) ou pluriel ($-1$).

- Un nouveau sujet : $f \approx 0$, $i \approx 1$, $\tilde{c} = \pm 1$, on efface puis on écrit la nouvelle valeur.
- Les mots intermédiaires : $f \approx 1$, $i \approx 0$, on conserve la valeur et le gradient peut circuler.
- Le verbe : $o \approx 1$, on montre la valeur pour accorder le verbe.

# Remarque

Comme pour la [[Perte absolue et perte quadratique|perte quadratique moyenne]], une zone plate signifie absence de gradient : la fonction ne transmet plus de signal d'apprentissage. Dans un réseau profond, cet effet se cumule couche après couche, ce qui rend le choix de l'activation déterminant. La dérivée de la sigmoïde, bornée par $0.25$, en est un cas typique ; à l'inverse, la pente $1$ de ReLU sur $z > 0$ n'éteint pas le gradient.

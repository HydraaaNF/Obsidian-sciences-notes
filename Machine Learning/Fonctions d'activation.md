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

- La sigmoïde est plate aux deux extrémités et sa dérivée est majorée : $\frac{d\sigma}{dz}(z) \le 0.25$ pour tout $z$.
- La tangente hyperbolique est centrée sur $0$ et présente elle aussi des extrémités plates.
- ReLU a une pente de $1$ pour $z > 0$ et reste peu coûteuse à calculer.

```chart
type: line
labels: ["-3.0", "-2.5", "-2.0", "-1.5", "-1.0", "-0.5", "0.0", "0.5", "1.0", "1.5", "2.0", "2.5", "3.0"]
series:
  - title: Sigmoïde
    data: [0.047, 0.076, 0.119, 0.182, 0.269, 0.378, 0.5, 0.622, 0.731, 0.818, 0.881, 0.924, 0.953]
    pointRadius: 0
    borderWidth: 2
  - title: Tanh
    data: [-0.995, -0.987, -0.964, -0.905, -0.762, -0.462, 0.0, 0.462, 0.762, 0.905, 0.964, 0.987, 0.995]
    pointRadius: 0
    borderWidth: 2
  - title: ReLU
    data: [0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.5, 1.0, 1.5, 2.0, 2.5, 3.0]
    pointRadius: 0
    borderWidth: 2
yMin: -1
yMax: 3
```

Les deux fonctions de type sigmoïde s'aplatissent loin de zéro, tandis que ReLU reste une droite de pente $1$ sur tout le demi-axe positif.

# Interprétation

Le choix de la fonction dépend de la couche et de ce que l'on veut représenter.

- Pour les couches cachées d'un [[Perceptron multicouche]], ReLU est le choix par défaut.
- La sigmoïde, à valeurs dans $(0, 1)$, se lit comme un cadran : elle dose une quantité entre « rien » et « tout ».
- La tangente hyperbolique, à valeurs dans $(-1, 1)$, fournit une valeur signée et bornée.

Un neurone dont l'activation est la sigmoïde calcule exactement une [[Régression logistique]] : toute valeur réelle du score est ramenée dans $(0, 1)$.

# Remarque

Comme pour la [[Perte absolue et perte quadratique|perte quadratique moyenne]], une zone plate signifie absence de gradient : la fonction ne transmet plus de signal d'apprentissage. Dans un réseau profond, cet effet se cumule couche après couche, ce qui rend le choix de l'activation déterminant. La dérivée de la sigmoïde, bornée par $0.25$, en est un cas typique ; à l'inverse, la pente $1$ de ReLU sur $z > 0$ n'éteint pas le gradient.

- Une [[Couche de convolution]] se termine par une de ces activations, appliquée à chaque carte de caractéristiques.
- Sans non-linéarité, la couche cachée ne changerait pas l'espace : c'est ce que montre le [[Problème du ou exclusif]].
- L'[[Unité récurrente à portes]] réduit la cellule à deux portes, calculées avec la sigmoïde, et à un contenu candidat calculé avec la tangente hyperbolique.

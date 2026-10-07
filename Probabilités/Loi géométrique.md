# Définition

La loi géométrique est la loi du nombre d'épreuves de [[Loi de Bernoulli|Bernoulli]] nécessaires pour obtenir le premier succès.

Pour une suite d'épreuves de Bernoulli indépendantes et de même probabilité de succès $p$, la probabilité que le premier succès survienne à la $k$-ième épreuve vaut

$$\mathbb{P}(X = k) = (1-p)^{k-1}p, \qquad k \in \mathbb{N}^*.$$

# Propriétés

Son [[Espérance d'une variable aléatoire|espérance]] et sa [[Variance|variance]] valent

$$\mathbb{E}(X) = \frac{1}{p}$$

$$\mathbb{V}(X) = \frac{1-p}{p^2}.$$

Sa [[Fonction génératrice|fonction génératrice]] vaut

$$G_X(z) = \mathbb{E}(z^X) = \frac{pz}{1-(1-p)z}.$$

# Liens avec d'autres lois

- La loi géométrique est le cas particulier $r = 1$ de la [[Loi binomiale négative|loi binomiale négative]], qui décrit le nombre d'épreuves de Bernoulli nécessaires pour obtenir le $r$-ième succès.
- Elle se distingue de la [[Loi binomiale|loi binomiale]], qui compte le nombre de succès obtenus sur un nombre fixé d'épreuves indépendantes.
- La somme de $r$ variables aléatoires [[Loi géométrique|géométriques]] indépendantes de paramètre $p$ suit la [[Loi binomiale négative|loi binomiale négative]] $\mathcal{BN}(r, p)$.
- Le minimum de deux variables aléatoires [[Indépendance de variables aléatoires|indépendantes]] de lois géométriques de paramètres $p$ et $q$ suit une loi géométrique de paramètre $1 - (1-p)(1-q)$.
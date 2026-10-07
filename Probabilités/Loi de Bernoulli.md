# Définition

La loi de Bernoulli est la loi d'une variable aléatoire binaire $X$, prenant la valeur 1 avec probabilité $p$ et la valeur 0 avec probabilité $1-p$ :

$$\mathbb{P}[X = k] = p^k(1-p)^{1-k}, \qquad k \in \{0, 1\}.$$

# Interprétation

La loi de Bernoulli est typiquement utilisée comme fonction indicatrice d'un événement se produisant avec probabilité $p$.

# Propriétés

- $\mathbb{E}[X] = p$ ;
- $\mathbb{V}[X] = p(1-p)$.

Sa [[Fonction génératrice|fonction génératrice]] vaut

$$G_X(z) = \mathbb{E}(z^X) = pz + (1-p).$$

# Liens avec d'autres lois

- La loi de Bernoulli est le cas particulier $n = 1$ de la [[Loi binomiale|loi binomiale]], qui décrit le nombre de succès sur $n$ épreuves de Bernoulli indépendantes, c'est-à-dire la loi de la somme de $n$ variables de Bernoulli indépendantes.
- La loi de Bernoulli de paramètre $p = \frac{1}{2}$ prend deux valeurs équiprobables et correspond au cas $n = 2$ de la [[Loi uniforme discrète|loi uniforme discrète]].
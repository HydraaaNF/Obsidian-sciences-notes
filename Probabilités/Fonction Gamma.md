# Définition

On appelle **fonction Gamma** la fonction $\Gamma$ définie sur $]0, +\infty[$ par

$$\forall \alpha > 0 \quad \Gamma(\alpha) = \int_0^{+\infty} t^{\alpha-1} e^{-t}\,dt$$

Elle prolonge à $]0, +\infty[$ la suite $((n - 1)!)_{n \in \mathbb{N}^*}$.

# Propriétés

**Relation de récurrence.**

$$\forall \alpha > 0 \quad \Gamma(\alpha + 1) = \alpha \Gamma(\alpha)$$

**Valeurs aux points entiers.**

$$\forall n \in \mathbb{N} \quad \Gamma(n + 1) = n!$$

**Valeur en $1/2$.**

$$\Gamma(1/2) = \sqrt{\pi}$$

**Formule de réflexion.** Pour $x \notin \mathbb{Z}$,

$$\Gamma(x)\,\Gamma(1-x) = \frac{\pi}{\sin(\pi x)}.$$

L'intégrale définissant $\Gamma(\alpha)$ ne se calcule pas à l'aide des fonctions usuelles, sauf dans le cas où $\alpha \in \mathbb{N}^*$ : elle vaut alors $(\alpha - 1)!$.

# Interprétation

En probabilités, la fonction $\Gamma$ fournit la constante de normalisation de la [[Probabilité à densité|densité]] de la [[Loi gamma|loi Gamma]] :

$$C = \frac{\beta^\alpha}{\Gamma(\alpha)}$$

C'est de cette fonction que la loi Gamma tire son nom. Elle apparaît également dans les moments de nombreuses lois usuelles : voir [[Loi de Weibull]] (espérance et variance) et [[Loi du chi-deux|loi du chi-deux]].

# Loi

Soit $n \in \mathbb{N}^*$ et $\lambda > 0$. $X \sim E(n, \lambda)$ si $X$ admet pour densité

$$f_X(x) = \frac{\lambda^n \, x^{n-1} \, e^{-\lambda x}}{(n-1)!}, \qquad x \geq 0$$

# Interprétation

X modélise le temps d'attente avant le $n$-ième évènement d'un processus de Poisson de taux $\lambda$ — c'est la généralisation naturelle de la [[Loi exponentielle]] (temps d'attente avant le premier évènement, cas $n=1$), de la même manière que la [[Loi binomiale négative]] généralise la [[Loi géométrique]] dans le cas discret.

# Caractérisation par la loi exponentielle

Soient $Y_1, \ldots, Y_n$ des variables i.i.d. $\sim \mathcal{E}(\lambda)$. Alors

$$X = \sum_{i=1}^{n} Y_i \; \sim \; E(n, \lambda)$$

Démonstration (via la fonction génératrice des moments) : par indépendance, la MGF d'une somme est le produit des MGF, donc

$$M_X(t) = \prod_{i=1}^{n} M_{Y_i}(t) = \left(\frac{\lambda}{\lambda - t}\right)^{n}$$

ce qui est exactement la MGF de $E(n, \lambda)$ donnée ci-dessous, et caractérise donc la loi.

# Dualité avec la loi de Poisson

Si $N(t)$ est un processus de Poisson de taux $\lambda$ et $T_n$ le temps d'attente du $n$-ième évènement, alors les évènements $\{N(t) \geq n\}$ et $\{T_n \leq t\}$ coïncident, d'où

$$\mathbb{P}(T_n \leq t) = \mathbb{P}(N(t) \geq n)$$

# Propriétés

Soit $X \sim E(n, \lambda)$, alors

* $\mathbb{E}(X) = \dfrac{n}{\lambda}$
* $\mathbb{V}(X) = \dfrac{n}{\lambda^2}$
* $M_X(t) = \left(\dfrac{\lambda}{\lambda - t}\right)^{n}, \quad t < \lambda$
* $\varphi_X(t) = \left(\dfrac{\lambda}{\lambda - it}\right)^{n}$

# Liens avec d'autres lois
* Cas particulier $n=1$ : $E(1, \lambda) = \mathcal{E}(\lambda)$
* Cas particulier de la [[Loi gamma]] à paramètre de forme entier : $E(n, \lambda) = \text{Gamma}(n, 1/\lambda)$

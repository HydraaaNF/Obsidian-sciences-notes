# Loi

Une [[Variable aléatoire continue|variable aléatoire continue]] suit la loi gamma de paramètre de forme $k > 0$ et de paramètre de taux $\lambda > 0$ lorsque sa [[Probabilité à densité|densité de probabilité]] s'écrit, pour $x > 0$,

$$f(x) = \frac{\lambda^k}{\Gamma(k)}\, x^{k-1} e^{-\lambda x},$$

où $\Gamma$ désigne la [[Fonction Gamma|fonction Gamma]] ; $f(x) = 0$ pour $x < 0$. Sa [[Fonction de répartition|fonction de répartition]] s'écrit $F(x) = \int_{-\infty}^{x} f(t)\, dt$.

# Interprétation

La loi gamma est en quelque sorte l'équivalent continu de la [[Loi de Poisson|loi de Poisson]] : pour $k$ entier, elle décrit le temps d'attente du $k$-ième événement d'un [[Processus de Poisson|processus de Poisson]] de taux $\lambda$, là où la loi de Poisson compte les événements survenant au cours du temps.

# Propriétés

Son [[Espérance d'une variable aléatoire|espérance]] et sa [[Variance|variance]] valent

$$\mathbb{E}(X) = \frac{k}{\lambda}$$

$$\mathbb{V}(X) = \frac{k}{\lambda^2}.$$

Sa [[Fonction caractéristique|fonction caractéristique]] vaut

$$\Phi_X(\xi) = \left(\frac{\lambda}{\lambda - i\xi}\right)^k.$$

Son mode vaut

$$\frac{k-1}{\lambda} \quad \text{pour } k \geq 1.$$

# Liens avec d'autres lois

La loi gamma généralise la [[Loi exponentielle|loi exponentielle]] : pour $k = 1$, elle coïncide avec la loi exponentielle de paramètre $\lambda$.

- La loi gamma de paramètre de forme entier $k$ est la loi de la somme de $k$ variables aléatoires [[Indépendance de variables aléatoires|indépendantes]] et identiquement distribuées de [[Loi exponentielle|loi exponentielle]] de paramètre $\lambda$.
- La somme de deux variables aléatoires indépendantes de lois gamma de même paramètre de taux $\lambda$ suit une loi gamma : si $X \sim \Gamma(k_1, \lambda)$ et $Y \sim \Gamma(k_2, \lambda)$, alors $X + Y \sim \Gamma(k_1 + k_2, \lambda)$.
- Elle coïncide avec la [[Loi du chi-deux|loi du chi-deux]] à $n$ degrés de liberté pour $k = n/2$ et $\lambda = 1/2$.
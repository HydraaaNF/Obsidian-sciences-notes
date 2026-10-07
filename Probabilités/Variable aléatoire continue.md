# Définition

Pour une [[Variable aléatoire]] continue $X$, la probabilité d'une valeur isolée est nulle : $\mathbb{P}[X = x] = 0$. La probabilité se définit sur un intervalle : $\mathbb{P}(x < X < x + dx) = f(x)dx$, où $f(x)$ est sa [[Probabilité à densité|densité de probabilité]] (pdf, *probability density function*).

Sa [[Fonction de répartition]] est $F(x) = \int_{-\infty}^x f(x)dx$ (cdf, *cumulative distribution function*).

# Propriétés

La probabilité que $X$ prenne une valeur entre $a$ et $b$ s'obtient en intégrant la densité :

$$\mathbb{P}(a < X < b) = \int_a^b f(x)\,dx = F(b) - F(a)$$

# Interprétation

$\mathbb{P}(a < X < b)$ se lit comme l'aire sous la courbe de la densité $f(x)$ entre les bornes $a$ et $b$ : l'aire hachurée entre $a$ et $b$ vaut la probabilité que $X$ appartienne à cet intervalle.

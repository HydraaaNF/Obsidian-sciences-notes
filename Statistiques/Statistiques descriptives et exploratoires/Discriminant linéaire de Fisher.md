# Définition

Soient des observations $\mathbf{x}_i$ issues de deux classes, de moyennes respectives $\mu_0$ et $\mu_1$ et de matrices de covariance respectives $\Sigma_0$ et $\Sigma_1$. La projection de ces observations le long de la droite dirigée par $\mathbf{w}$ produit une séparation définie par

$$S = \frac{\sigma_{\text{across}}}{\sigma_{\text{within}}} = \frac{(\mathbf{w}(\mu_1 - \mu_0))^2}{\mathbf{w}^\top(\Sigma_0 + \Sigma_1)\mathbf{w}}.$$

Le rapport $S$ compare la [[Variance et écart-type|dispersion]] entre les deux classes ($\sigma_{\text{across}}$) à la dispersion au sein de chaque classe ($\sigma_{\text{within}}$).

# Propriétés

La séparation est maximale pour

$$\mathbf{w} = (\Sigma_0 + \Sigma_1)^{-1}(\mu_1 - \mu_0).$$

# Remarque

Le discriminant linéaire de Fisher est le cas particulier à deux classes de l'[[Analyse discriminante linéaire]] ; il en est équivalent sous l'hypothèse que la distribution *a posteriori* $p(x_i \mid \text{classe})$ est gaussienne et homoscédastique ($\Sigma_0 = \Sigma_1 = \Sigma$).

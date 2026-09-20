# Définition
Cas à 2 classes de moyennes $\mu_0$, $\mu_1$ et de matrices de covariance $\Sigma_0$, $\Sigma_1$. Une projection sur la droite $w$ induit une séparation
$$S = \frac{\sigma_{across}}{\sigma_{within}} = \frac{(w'(\mu_1-\mu_0))^2}{w'(\Sigma_0+\Sigma_1)w}$$

La séparation maximale est atteinte pour
$$w = (\Sigma_0 + \Sigma_1)^{-1}(\mu_1 - \mu_0)$$

# Remarque
La [[Analyse discriminante linéaire|LDA]] à 2 classes équivaut au discriminant de Fisher sous l'hypothèse que la distribution *a posteriori* $p(x_i \mid \text{classe})$ est gaussienne et homoscédastique ($\Sigma_0 = \Sigma_1 = \Sigma$).

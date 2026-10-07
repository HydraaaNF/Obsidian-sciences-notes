# Définition

La distance en moyenne d'ordre $p$ ($p \geq 1$) entre deux [[Variable aléatoire réelle|variables aléatoires]] est définie par

$$\|X - Y\|_p = \mathbb{E}[|X - Y|^p]^{1/p}.$$

Cette distance est définie sur l'espace métrique $L^p(\Omega, \mathbb{R})$ des variables aléatoires admettant un [[Moment d'ordre k|moment]] d'ordre $p$.

Pour $p = 2$, on parle de distance en moyenne quadratique.

# Interprétation

Soit $T$ un [[Estimateur|estimateur]] de $\theta$. Afin de définir la précision de l'estimateur, il faut choisir une distance $d$ et calculer $d(T, \theta)$. Afin que cette mesure de la précision de l'estimateur ne dépende pas des observations, on considère une distance en moyenne.

# Remarque

Soit $(X_n)$ une suite de variables aléatoires [[Convergence en moyenne d'ordre p|convergeant en moyenne d'ordre $p$]] vers une variable aléatoire $Y$, c'est-à-dire

$$\lim_{n \to \infty} \mathbb{E}[|X_n - Y|^p]^{1/p} = 0.$$

Cela est équivalent à la convergence dans $L^p(\Omega, \mathbb{R})$, notée

$$X_n \xrightarrow{L^p} Y.$$

Pour $p = 2$, la distance en moyenne quadratique est utilisée pour définir l'[[Erreur quadratique moyenne]] d'un estimateur.

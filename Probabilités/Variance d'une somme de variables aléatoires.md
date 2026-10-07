# Propriétés

Pour deux variables aléatoires $X$ et $Y$, la [[Variance|variance]] de leur somme vaut

$$\mathbb{V}[X+Y] = \mathbb{V}[X] + \mathbb{V}[Y] + 2\underbrace{\left(\mathbb{E}[XY] - \mathbb{E}[X]\mathbb{E}[Y]\right)}_{\operatorname{COV}(X,Y)}$$

où $\operatorname{COV}(X,Y)$ est la [[Covariance|covariance]] de $X$ et $Y$.

Lorsque $X$ et $Y$ sont [[Indépendance de variables aléatoires|indépendantes]] :

$$\mathbb{V}[X+Y] = \mathbb{V}[X] + \mathbb{V}[Y].$$

# Remarque

La réciproque est fausse : l'additivité $\mathbb{V}[X+Y] = \mathbb{V}[X] + \mathbb{V}[Y]$ n'implique pas que $X$ et $Y$ sont indépendantes ; elle équivaut à l'annulation de leur [[Covariance|covariance]], c'est-à-dire à la non-corrélation de $X$ et $Y$, une condition plus faible que l'indépendance (voir [[Variables aléatoires non corrélées]]).

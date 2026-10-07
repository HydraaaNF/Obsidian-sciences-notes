# Définition

La **covariance** de deux variables aléatoires $X$ et $Y$ est définie par

$$\operatorname{COV}(X,Y) = \mathbb{E}[XY] - \mathbb{E}[X]\mathbb{E}[Y].$$

# Propriétés

La covariance apparaît dans la [[Variance d'une somme de variables aléatoires|variance d'une somme]] de deux variables aléatoires :

$$\mathbb{V}[X + Y] = \mathbb{V}[X] + \mathbb{V}[Y] + 2\operatorname{COV}(X,Y).$$

En particulier, si $X$ et $Y$ sont [[Indépendance de variables aléatoires|indépendantes]], alors $\mathbb{V}[X + Y] = \mathbb{V}[X] + \mathbb{V}[Y]$ et donc $\operatorname{COV}(X,Y) = 0$ ; la réciproque est fausse.

# Remarque

- Les variables dont la covariance est nulle sont dites [[Variables aléatoires non corrélées|non corrélées]].
- Le [[Coefficient de corrélation linéaire]] s'obtient en normalisant la covariance par le produit des [[Variance|écarts-types]] de $X$ et de $Y$.

# Définition

Soient $X$ et $Y$ deux [[Variable aléatoire réelle|variables aléatoires réelles]] admettant un [[Moment d'ordre k|moment d'ordre 2]]. On appelle **coefficient de corrélation linéaire** de $X$ et de $Y$ la quantité

$$r_{X,Y} = \frac{\operatorname{cov}(X, Y)}{\sigma_X \sigma_Y}$$

où $\operatorname{cov}(X, Y) = \mathbb{E}((X - \mathbb{E}(X))(Y - \mathbb{E}(Y)))$ est la [[Covariance|covariance]] de $X$ et de $Y$, et où $\sigma_X$ et $\sigma_Y$ sont leurs [[Variance|écarts-types]] respectifs.

# Propriétés

L'[[Inégalité de Cauchy-Schwarz pour des variables aléatoires|inégalité de Cauchy-Schwarz]] donne

$$|\operatorname{cov}(X, Y)| \leq \sigma_X \sigma_Y$$

Autrement dit :

$$-1 \leq r_{X,Y} \leq 1$$

# Interprétation

Supposons que l'on observe un grand nombre de réalisations $(x_1, y_1), \ldots, (x_p, y_p)$ du couple aléatoire $(X, Y)$. On peut partager le plan en quatre régions :

- celle où les points $(x_i, y_i)$ sont tels que $x_i \geq \mathbb{E}(X)$ et $y_i \geq \mathbb{E}(Y)$ ;
- celle où les points $(x_i, y_i)$ sont tels que $x_i \geq \mathbb{E}(X)$ et $y_i \leq \mathbb{E}(Y)$ ;
- celle où les points $(x_i, y_i)$ sont tels que $x_i \leq \mathbb{E}(X)$ et $y_i \geq \mathbb{E}(Y)$ ;
- et celle où les points $(x_i, y_i)$ sont tels que $x_i \leq \mathbb{E}(X)$ et $y_i \leq \mathbb{E}(Y)$.

La covariance nous renseigne donc sur la tendance, s'il y en a une, qu'ont les points à tomber dans une partie du plan plutôt qu'une autre, autour du [[Vecteur moyen|vecteur moyen]] $(\mathbb{E}(X), \mathbb{E}(Y))$.

Dans le même esprit, le coefficient de corrélation linéaire est une quantité sans dimension, analogue à un « cosinus » (c'est le produit scalaire dans $L^2(\Omega, \mathbb{P})$ des variables aléatoires $X - \mathbb{E}(X)$ et $Y - \mathbb{E}(Y)$, divisé par le produit de leurs normes), qui nous renseigne sur une éventuelle tendance linéaire lorsqu'il est proche de $\pm 1$.

# Remarque

Lorsque la covariance de $X$ et de $Y$ est nulle, le coefficient de corrélation linéaire est nul : les deux variables sont alors dites [[Variables aléatoires non corrélées|non corrélées]].

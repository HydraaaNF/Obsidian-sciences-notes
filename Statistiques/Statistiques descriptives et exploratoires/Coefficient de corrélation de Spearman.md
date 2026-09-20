# Définition
Soit $r(x_i)$ le rang de $x_i$ dans l'échantillon trié (idem pour $y_i$). Le coefficient de Spearman est
$$\rho_{XY} = 1 - \frac{6\sum_{i=1}^{n}(r(x_i) - r(y_i))^2}{n(n^2-1)}$$

# Interprétation
Mesure les dépendances **monotones non linéaires** entre $X$ et $Y$ (contrairement à Pearson, limité au linéaire), et est moins sensible aux valeurs aberrantes puisqu'il ne travaille que sur les rangs.

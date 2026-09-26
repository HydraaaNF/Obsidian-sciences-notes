# Définition
Soit $r(x_i)$ le rang de $x_i$ dans l'échantillon trié (idem pour $y_i$). Le coefficient de Spearman est
$$\rho_{XY} = 1 - \frac{6\sum_{i=1}^{n}(r(x_i) - r(y_i))^2}{n(n^2-1)}$$

# Interprétation
Mesure les dépendances **monotones non linéaires** entre $X$ et $Y$ (contrairement à Pearson, limité au linéaire), et est moins sensible aux valeurs aberrantes puisqu'il ne travaille que sur les rangs.

# Exemple
10 vins classés par deux experts :

| $x_i$ | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---|---|---|---|---|---|---|---|---|---|
| $y_i$ | 3 | 1 | 4 | 2 | 6 | 5 | 9 | 8 | 10 | 7 |

On obtient $\rho_{XY} = 0{,}84$ : les deux classements sont fortement concordants.

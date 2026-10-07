# Définition

Pour deux caractères quantitatifs $X$ et $Y$ observés sur $n$ individus, le **coefficient de corrélation des rangs de Spearman** est la quantité

$$\rho_{XY} = 1 - \frac{6 \sum_{i=1}^n (r(x_i) - r(y_i))^2}{n(n^2 - 1)}$$

où $r(x_i)$ désigne le rang de $x_i$ parmi les observations de $X$, et $r(y_i)$ le rang de $y_i$ parmi les observations de $Y$.

# Interprétation

Il mesure les dépendances monotones, y compris non linéaires, là où le [[Covariance et coefficient de corrélation linéaire|coefficient de corrélation linéaire de Pearson]] ne reflète que les dépendances linéaires.

Parce qu'il ne fait intervenir que les rangs des observations, il est moins sensible aux valeurs extrêmes.

# Exemple

Dix vins sont classés par deux experts ; les rangs $x_i$ et $y_i$ attribués aux vins sont :

| $x_i$ | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---|---|---|---|---|---|---|---|---|---|
| $y_i$ | 3 | 1 | 4 | 2 | 6 | 5 | 9 | 8 | 10 | 7 |

Pour ces deux classements, le coefficient de Spearman vaut $\rho = 0{,}84$. La [[Corrélation des rangs de Kendall|corrélation des rangs de Kendall]], calculée sur les mêmes données, vaut $\tau = 0{,}64$.

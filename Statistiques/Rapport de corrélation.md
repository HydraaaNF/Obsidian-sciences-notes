# Définition
Pour $X$ catégorielle (à $k$ catégories, la catégorie $i$ regroupant $n_i$ individus) et $Y$ numérique de moyenne $\mu_Y$ :
$$\eta^2_{Y|X} = \frac{\frac{1}{n}\sum_i n_i (\mu_{Y|X=i} - \mu_Y)^2}{\sigma_Y^2}$$

# Interprétation
Mesure la dépendance entre une variable catégorielle et une variable numérique (cas mixte, où les coefficients de [[Coefficient de corrélation de Pearson|Pearson]], [[Coefficient de corrélation de Spearman|Spearman]] ou [[Coefficient de corrélation de Kendall|Kendall]] ne s'appliquent pas directement).

- $\eta = 0$ : les moyennes de $Y$ sont identiques dans chaque catégorie de $X$ (pas de dispersion entre catégories)
- $\eta = 1$ : $Y$ est constant à l'intérieur de chaque catégorie de $X$ (pas de dispersion au sein des catégories)

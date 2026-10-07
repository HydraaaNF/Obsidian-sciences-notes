# Définition

Le **rapport de corrélation** mesure la [[Corrélation de deux caractères|corrélation]] entre deux caractères dans les situations mixtes, où le caractère $X$ est [[Caractère qualitatif|catégoriel]] et le caractère $Y$ est numérique. Il compare la dispersion des [[Moyenne et variance conditionnelles|moyennes conditionnelles]] de $Y$ entre les catégories de $X$ à la dispersion totale de $Y$ :

$$\eta_{Y\mid X}^{2} = \frac{\frac{1}{n}\sum_i n_i\left(\bar{\mu}_{Y\mid X=i}-\bar{\mu}_Y\right)^2}{\frac{1}{n}\sum_y\left(y-\bar{\mu}_Y\right)^2} = \frac{\sigma_{\bar{\mu}_{Y\mid X=i}}^{2}}{\sigma_Y^{2}}$$

où $n_i$ est l'effectif de la catégorie $i$, $\bar{\mu}_{Y\mid X=i}$ la moyenne conditionnelle de $Y$ dans la catégorie $i$, $\bar{\mu}_Y$ la moyenne globale de $Y$, $\sigma_{\bar{\mu}_{Y\mid X=i}}^2$ la variance des moyennes conditionnelles et $\sigma_Y^2$ la [[Variance et écart-type|variance]] de $Y$.

# Interprétation

Le rapport de corrélation traduit la part de la dispersion totale de $Y$ qui provient des différences de moyennes entre les catégories de $X$ :

- $\eta = 0$ : pas de dispersion des moyennes entre les catégories, les moyennes conditionnelles $\bar{\mu}_{Y\mid X=i}$ sont toutes égales ;
- $\eta = 1$ : pas de dispersion à l'intérieur des catégories respectives, $Y$ ne varie pas au sein d'une même catégorie.

Il complète, pour les couples mixtes, les mesures d'association entre deux caractères numériques telles que le [[Coefficient de corrélation des rangs de Spearman]].

# Remarque

La forme usuelle du rapport de corrélation est le quotient de deux variances empiriques : au dénominateur, la variance de $Y$ est

$$\sigma_Y^2 = \frac{1}{n}\sum_y\left(y-\bar{\mu}_Y\right)^2.$$

L'écriture où le dénominateur reste la somme des carrés des écarts $\sum_y\left(y-\bar{\mu}_Y\right)^2$, sans division par $n$, omet cette normalisation : le quotient vaut alors $\eta_{Y\mid X}^2/n$, et non $\sigma_{\bar{\mu}_{Y\mid X=i}}^2/\sigma_Y^2$.

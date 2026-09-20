# Définition
Pour un échantillon $(x_i, y_i)_{1 \leq i \leq n}$ de moyennes $\bar{\mu}_x$, $\bar{\mu}_y$ et d'écarts-types empiriques $\hat{\sigma}_x$, $\hat{\sigma}_y$ :
$$r_{XY} = \frac{\frac{1}{n}\sum_{i=1}^{n}(x_i - \bar{\mu}_x)(y_i - \bar{\mu}_y)}{\hat{\sigma}_x \hat{\sigma}_y}$$

# Interprétation
Mesure la force et le sens d'une relation **linéaire** entre $X$ et $Y$, $r_{XY} \in [-1, 1]$.

# Remarque
Ne détecte que les dépendances linéaires : une dépendance non linéaire forte peut donner un $r_{XY}$ proche de 0. Voir [[Coefficient de corrélation de Spearman]] pour une alternative robuste aux relations monotones non linéaires.

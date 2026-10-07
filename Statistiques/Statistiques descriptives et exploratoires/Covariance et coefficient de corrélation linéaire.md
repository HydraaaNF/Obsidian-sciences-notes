# Définition

Pour deux caractères quantitatifs $X$ et $Y$ observés sur $n$ individus, dont les observations forment les couples $(x_1, y_1), \dots, (x_n, y_n)$, le **coefficient de corrélation linéaire de Pearson** est la quantité

$$r_{XY} = \frac{\frac{1}{n} \sum_{i=1}^n (x_i - \hat{\mu}_x)(y_i - \hat{\mu}_y)}{\hat{\sigma}_x \hat{\sigma}_y}$$

où $\hat{\mu}_x$ et $\hat{\mu}_y$ sont les [[Moyenne empirique|moyennes empiriques]] de $X$ et de $Y$, et où $\hat{\sigma}_x$ et $\hat{\sigma}_y$ sont leurs [[Variance et écart-type|écarts-types empiriques]]. Le numérateur est la [[Covariance empirique|covariance empirique]] de $X$ et de $Y$.

# Interprétation

Il mesure la force et la direction de la [[Corrélation de deux caractères|corrélation]] entre les deux caractères : son signe indique le sens de la liaison et sa valeur absolue en donne la force.

Il ne s'applique qu'aux dépendances linéaires : une dépendance non linéaire n'est pas reflétée par sa valeur.

# Exemple

Quatre [[Nuage de points|nuages de points]] illustrent des configurations typiques :

- un nuage allongé le long d'une droite croissante, avec des écarts individuels notables autour de celle-ci ;
- un nuage en arc de courbe, dont la tendance n'est pas linéaire ;
- des observations presque alignées sur une droite croissante, dont une nettement au-dessus de l'alignement ;
- des observations concentrées sur une même abscisse, complétées d'une observation isolée vers la droite, la même droite croissante reliant les deux groupes.

# Remarque

- La forme usuelle du coefficient divise la covariance empirique par le produit des écarts-types empiriques $\hat{\sigma}_x \hat{\sigma}_y$ ; l'écriture avec le produit des variances $\hat{\sigma}_x^2 \hat{\sigma}_y^2$ au dénominateur est une erreur fréquente, car elle ne garantit pas que $r_{XY}$ reste compris entre $-1$ et $1$.
- C'est l'analogue empirique, pour des observations, de la [[Covariance]] et du [[Coefficient de corrélation linéaire]] d'un couple de variables aléatoires.
- Les coefficients de plusieurs caractères observés ensemble se rassemblent dans une [[Matrice de corrélation]] ; l'ajustement de la liaison linéaire correspondante conduit à la [[Droite de régression de y en x]].

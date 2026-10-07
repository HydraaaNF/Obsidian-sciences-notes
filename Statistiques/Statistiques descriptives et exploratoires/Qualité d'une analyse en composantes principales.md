# Propriétés

La qualité de la représentation fournie par une [[Analyse en composantes principales|analyse en composantes principales]] se mesure globalement, pour l'ensemble du nuage, et localement, pour un échantillon donné :

- **Fraction d'inertie totale retenue** (mesure globale) :

$$\frac{\lambda_1+\cdots+\lambda_q}{\ell_g}$$

où $\lambda_1, \dots, \lambda_q$ sont les valeurs propres associées aux $q$ axes retenus et $\ell_g$ l'inertie totale du nuage ;

- **Angle entre le plan principal et un échantillon** (mesure locale) : plus cet angle est petit, meilleure est la représentation de l'échantillon ;
- **Erreur de reconstruction d'un échantillon** (mesure locale) :

$$\|\mathbf{x}_i - \bar{U}^T \mathbf{y}_i\| = \|\mathbf{x}_i - \bar{U}^T \bar{U} \mathbf{x}_i\|$$

où $\bar{U}$ est la matrice des $q$ premiers axes et $\mathbf{y}_i$ la projection de l'échantillon $\mathbf{x}_i$.

# Interprétation

La fraction d'inertie totale retenue est une mesure **globale** : elle quantifie la part de l'inertie du nuage restituée par les $q$ axes retenus, et sert de critère pour choisir le nombre de composantes (voir l'[[Éboulis des valeurs propres]]). L'angle entre le plan principal et un échantillon ainsi que l'erreur de reconstruction sont des mesures **locales** : elles évaluent la représentation d'un échantillon particulier.

# Remarque

Le plan principal, les axes et les composantes principales sont définis dans le [[Vocabulaire de l'analyse en composantes principales]] ; la matrice $\bar{U}$ des axes retenus est construite par l'[[Algorithme de l'analyse en composantes principales]].

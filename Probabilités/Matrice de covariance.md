# Définition

La matrice de covariance $\Sigma$ d'un [[Vecteur aléatoire|vecteur aléatoire]] $X = (X_1, \dots, X_p)$ est la matrice de terme général

$$\Sigma_{ij} = \operatorname{COV}(X_i, X_j).$$

Ses coefficients diagonaux sont les variances des composantes et ses coefficients hors diagonale leurs [[Covariance|covariances]] deux à deux.

# Propriétés

La matrice de covariance est symétrique et définie positive. Elle se décompose sous la forme

$$\Sigma = V D V^\top$$

où $V$ sont les vecteurs propres définissant les axes principaux (orientation de la [[Densité d'un vecteur gaussien|densité]]) et $D$ sont les valeurs propres définissant la dispersion le long des axes.

# Exemple

En dimension 2, la matrice de covariance d'un [[Vecteur gaussien]] s'écrit, du point de vue de la corrélation,

$$\Sigma = \begin{pmatrix} \sigma_1^2 & \rho\sigma_1\sigma_2 \\ \rho\sigma_2\sigma_1 & \sigma_2^2 \end{pmatrix}$$

où $\rho$ est le [[Coefficient de corrélation linéaire|coefficient de corrélation linéaire]] des deux composantes et $\sigma_1$, $\sigma_2$ leurs écarts-types. Du point de vue géométrique, les vecteurs propres définissant les axes principaux forment la matrice

$$V = \begin{pmatrix} \cos(\theta) & -\sin(\theta) \\ \sin(\theta) & \cos(\theta) \end{pmatrix}$$

L'orientation de la densité est fixée par $\theta$ et la dispersion par $D$. Les trois cas illustrés sont :

| $\theta$ | $D$ | Forme de la densité |
|---|---|---|
| $0$ | $\operatorname{diag}(4 \quad 1)$ | densité allongée selon le premier axe principal |
| $\pi/6$ | $\operatorname{diag}(4 \quad 1)$ | même dispersion, axes principaux tournés de $\pi/6$ |
| $\pi/6$ | $\operatorname{diag}(2 \quad 2)$ | dispersion isotrope, cloche à symétrie circulaire |

## Lecture des coefficients en dimension 2

La diagonalisation $\Sigma = V D V^\top$ s'écrit, avec $D = \operatorname{diag}(\lambda_1, \lambda_2)$,

$$\Sigma = \lambda_1 v_1 v_1^\top + \lambda_2 v_2 v_2^\top.$$

En développant le produit, on lit directement les coefficients de la matrice de covariance :

$$\sigma_1^2 = \lambda_1\cos^2\theta + \lambda_2\sin^2\theta, \qquad \sigma_2^2 = \lambda_1\sin^2\theta + \lambda_2\cos^2\theta, \qquad \rho\sigma_1\sigma_2 = (\lambda_1-\lambda_2)\sin\theta\cos\theta.$$

Ainsi, $D$ indique combien la densité s'étire, $V$ dans quelles directions, et $\theta$ comment ces directions sont orientées dans le plan.

# Remarque

- La matrice des vecteurs propres est orthogonale : ses colonnes forment une base orthonormée d'axes principaux. La forme $V = \begin{pmatrix} \cos\theta & \sin\theta \\ \sin\theta & \cos\theta \end{pmatrix}$ est une erreur fréquente : ses colonnes ne sont pas orthogonales, leur produit scalaire valant $\sin(2\theta)$ ; la forme correcte est $V = \begin{pmatrix} \cos\theta & -\sin\theta \\ \sin\theta & \cos\theta \end{pmatrix}$.
- Lorsque $\Sigma$ est diagonale, les composantes sont [[Variables aléatoires non corrélées|non corrélées]] ; pour le lien avec l'indépendance des composantes d'un [[Vecteur gaussien]], voir [[Indépendance des coordonnées d'un vecteur gaussien]].

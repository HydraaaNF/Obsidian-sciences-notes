# Définition

La *courbe de régression* de $y$ en $x$ est la courbe représentant les [[Moyenne et variance conditionnelles|moyennes conditionnelles]] $\bar{y}_i$ en fonction des modalités $\alpha_i$ du caractère $X$. On la note $C_{y|x}$.

Si les caractères $X$ et $Y$ sont [[Indépendance de deux caractères|indépendants]], alors la courbe de régression de $y$ en $x$ (respectivement de $x$ en $y$) est la droite d'équation $y = \bar{y}$ (respectivement $x = \bar{x}$). Cependant, la réciproque est fausse.

# Propriétés

La courbe de régression de $y$ en $x$ est la courbe de la forme

$$y = \varphi(x)$$

qui ajuste au mieux le [[Nuage de points|nuage de points]] des observations au sens des moindres carrés. Autrement dit, la moyenne des carrés des distances entre $(x_i, y_i)$ et $(x_i, \varphi(x_i))$ est minimisée par la fonction $\varphi$ définie par

$$\varphi(\alpha_i) = \bar{y}_i$$

pour $i$ allant de $1$ à $k$.

### Démonstration

Soit $D$ la distance à minimiser :

$$\begin{aligned}
 D &= \frac{1}{n} \sum_{i=1}^n \|(x_i, y_i) - (x_i, \varphi(x_i))\|^2 \\
 &= \frac{1}{n} \sum_{i=1}^n (y_i - \varphi(x_i))^2 \\
 &= \frac{1}{n} \sum_{i=1}^k \sum_{j=1}^l n_{i,j} (\beta_j - \varphi(\alpha_i))^2 \\
 &= \sum_{i=1}^k \sum_{j=1}^l f_{i,j} (\beta_j - \varphi(\alpha_i))^2 \\
 &= \sum_{i=1}^k \sum_{j=1}^l f_{j|i} f_{i.} (\beta_j - \varphi(\alpha_i))^2 \\
 &= \sum_{j=1}^l f_{.j} \beta_j^2 - 2 \sum_{i=1}^k f_{i.} \varphi(\alpha_i) \sum_{j=1}^l f_{j|i} \beta_j + \sum_{i=1}^k f_{i.} \varphi(\alpha_i)^2 \sum_{j=1}^l f_{j|i} \\
 &= \mathbb{V}(y) + \bar{y}^2 - 2 \sum_{i=1}^k f_{i.} \varphi(\alpha_i) \bar{y}_i + \sum_{i=1}^k f_{i.} \varphi(\alpha_i)^2 \\
 &= \mathbb{V}(y) - \sum_{i=1}^k f_{i.} (\bar{y}_i - \bar{y})^2 + \sum_{i=1}^k f_{i.} (\bar{y}_i - \varphi(x_i))^2 .
\end{aligned}$$

La distance $D$ est la somme de termes positifs et atteint sa valeur minimale pour $\varphi(x_i) = \bar{y}_i$, c'est-à-dire pour la courbe de régression de $y$ en $x$.

# Remarque

Dans la décomposition de $D$, la simplification qui remplace $\bar{y}^2$ par $\sum_{i=1}^k f_{i.} \bar{y}_i^2$ est une erreur fréquente : ces deux quantités diffèrent de la variance des moyennes conditionnelles $\sum_{i=1}^k f_{i.} (\bar{y}_i - \bar{y})^2$, en général non nulle. La forme usuelle est

$$D = \mathbb{V}(y) - \sum_{i=1}^k f_{i.} (\bar{y}_i - \bar{y})^2 + \sum_{i=1}^k f_{i.} (\bar{y}_i - \varphi(x_i))^2 .$$

Le terme $\mathbb{V}(y) - \sum_{i=1}^k f_{i.} (\bar{y}_i - \bar{y})^2$ est constant en $\varphi$ : le minimum de $D$ est donc bien atteint pour $\varphi(\alpha_i) = \bar{y}_i$.

Lorsqu'une relation linéaire est recherchée entre les deux caractères, l'ajustement conduit à la [[Droite de régression de y en x]] ; l'étude de la liaison linéaire correspondante se poursuit avec la [[Covariance et coefficient de corrélation linéaire]].

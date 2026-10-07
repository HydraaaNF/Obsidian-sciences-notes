# Définition

Soit $X = (X_1, \ldots, X_n)$ un [[Vecteur aléatoire|vecteur aléatoire]] de $\mathbb{R}^n$ tel que chaque [[Variable aléatoire réelle|variable aléatoire réelle]] $X_j$ est intégrable (c'est-à-dire admet une [[Espérance d'une variable aléatoire|espérance]]). On appelle **espérance du vecteur** $X$, ou **vecteur moyen**, le vecteur de $\mathbb{R}^n$

$$\mathbb{E}(X) = (\mathbb{E}(X_1), \ldots, \mathbb{E}(X_n))$$

# Exemple

Soit $(X, Y)$ de [[Loi uniforme sur un domaine|loi uniforme]] sur le disque $D_R$ de centre $(0, 0)$ et de rayon $R$. À partir des [[Lois marginales|densités marginales]] de $X$ et de $Y$, il est immédiat que $X$ et $Y$, qui ont même loi, admettent une espérance, et qu'elle est nulle :

$$\mathbb{E}(X) = \int_{-R}^R x \frac{1}{\pi R^2} 2\sqrt{R^2 - x^2} dx = 0$$

puisque la fonction que l'on intègre sur $[-R, R]$ est impaire (l'existence provient du fait que $\int_{-R}^R |x| \sqrt{R^2 - x^2} dx < +\infty$ : c'est l'intégrale d'une fonction continue sur un intervalle compact).

Par conséquent le vecteur moyen est $\mathbb{E}((X, Y)) = (0, 0)$, ce qui est logique. On dit que $(X, Y)$ est *centré*.

# Remarque

Pour la dispersion d'un vecteur aléatoire autour de son vecteur moyen, voir la [[Matrice de covariance]].

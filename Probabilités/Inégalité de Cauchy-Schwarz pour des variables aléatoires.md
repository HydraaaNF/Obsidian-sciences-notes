# Théorème

L'inégalité de Cauchy-Schwarz, résultat général de la théorie de la mesure, se traduit en probabilités de la façon suivante (résultat admis).

Pour tout couple $(X, Y)$ de [[Variable aléatoire réelle|variables aléatoires réelles]], on a

$$\mathbb{E}(|XY|) \leq \sqrt{\mathbb{E}(X^2)\mathbb{E}(Y^2)}$$

# Remarque

1. Le membre de droite de l'inégalité peut être $+\infty$ si l'une des deux variables aléatoires n'a pas de [[Moment d'ordre k|moment d'ordre 2]] ; l'inégalité peut même se réduire à $+\infty \leq +\infty$, auquel cas elle est encore vraie.
2. Si $\mathbb{E}(|XY|) < +\infty$, on a de plus

$$|\mathbb{E}(XY)| \leq \mathbb{E}(|XY|)$$

Pour des variables aléatoires indépendantes, le calcul de l'espérance du produit est détaillé dans [[Espérance d'un produit de variables aléatoires indépendantes]].

# Propriétés

Si $X$ et $Y$ admettent un [[Moment d'ordre k|moment d'ordre 2]], alors l'[[Espérance d'une variable aléatoire|espérance]] de $(X - \mathbb{E}(X))(Y - \mathbb{E}(Y))$ existe (elle est finie). C'est cette quantité qui définit la [[Covariance]] de $X$ et de $Y$.

### Démonstration

En appliquant l'inégalité aux variables aléatoires $X - \mathbb{E}(X)$ et $Y - \mathbb{E}(Y)$, on obtient

$$\mathbb{E}(|(X - \mathbb{E}(X))(Y - \mathbb{E}(Y))|) \leq \sqrt{\mathbb{E}((X - \mathbb{E}(X))^2) \mathbb{E}((Y - \mathbb{E}(Y))^2)} < +\infty$$

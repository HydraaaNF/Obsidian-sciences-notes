# Propriétés

Soient $X$ et $Y$ les deux caractères d'une [[Série statistique double]], de modalités respectives $\alpha_1, \dots, \alpha_k$ et $\beta_1, \dots, \beta_l$. Pour chaque modalité $\beta_j$ du caractère $Y$, $j$ allant de $1$ à $l$, on dispose des moyenne et variance conditionnelles $\bar{x}_j$ et $V(x)_j$ des observations de $X$ conditionnellement à $\beta_j$ (voir [[Distributions conditionnelles]]). La [[Moyenne, médiane et mode|moyenne]] et la [[Variance et écart-type|variance]] de l'ensemble des observations $x_1, \dots, x_n$ de $X$ sont données par

$$\bar{x} = \frac{1}{n} \sum_{j=1}^l n_{.j} \bar{x}_j$$

et

$$V(x) = \frac{1}{n} \sum_{j=1}^l n_{.j} V(x)_j + \frac{1}{n} \sum_{j=1}^l n_{.j} (\bar{x}_j - \bar{x})^2 .$$

# Interprétation

La première relation s'énonce : *moyenne marginale = moyenne des moyennes conditionnelles*. La moyenne globale de $X$ est donc la moyenne des moyennes conditionnelles $\bar{x}_j$, pondérées par les effectifs conditionnels $n_{.j}$.

La seconde s'énonce : *variance marginale = moyenne des variances conditionnelles + variance des moyennes conditionnelles*. La dispersion globale des observations de $X$ se décompose ainsi en deux contributions :
- la **moyenne des variances conditionnelles** $\frac{1}{n} \sum_{j=1}^l n_{.j} V(x)_j$, dispersion des observations à l'intérieur de chaque distribution conditionnelle ;
- la **variance des moyennes conditionnelles** $\frac{1}{n} \sum_{j=1}^l n_{.j} (\bar{x}_j - \bar{x})^2$, dispersion des moyennes conditionnelles autour de la moyenne globale.

# Remarque

La décomposition de la variance marginale suit le même principe que celle de la [[Moyenne et variance d'une population composite|variance d'une population composite]] en sous-populations : la variance totale y est également la somme de la moyenne des variances internes et de la variance des moyennes.

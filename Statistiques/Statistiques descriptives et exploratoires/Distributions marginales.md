# Définition

Dans une [[Série statistique double|série statistique double]] $(X, Y)$, on appelle **distributions marginales** les distributions du [[Population statistique et caractère|caractère]] $X$ seul et du caractère $Y$ seul : chaque distribution marginale décrit un caractère pris isolément, en ignorant l'autre. Leurs indicateurs sont les indicateurs associés aux observations $x_1, \dots, x_n$ du caractère $X$ et les indicateurs associés aux observations $y_1, \dots, y_n$ du caractère $Y$.

# Interprétation

La moyenne marginale $\bar{x}$ est la [[Moyenne, médiane et mode|moyenne arithmétique]] des observations de $X$, et $\mathbb{V}(x)$ la [[Variance et écart-type|variance]] de ces observations : les indicateurs marginaux coïncident avec ceux des séries unidimensionnelles obtenues en considérant chaque caractère séparément.

# Propriétés

Les indicateurs marginaux se calculent directement sur les observations, ou de façon équivalente à partir des totaux $n_{i.}$ et $n_{.j}$ du [[Tableau de contingence]] et des fréquences marginales $f_{i.} = n_{i.}/n$, $f_{.j} = n_{.j}/n$ (voir [[Fréquences conjointes, marginales et conditionnelles]]).

## Moyennes marginales

Pour $X$, on a observé les classes $\alpha_1, \dots, \alpha_k$ avec les effectifs respectifs $n_{1.}, \dots, n_{k.}$ :

$$\bar{x} = \frac{1}{n} \sum_{i=1}^n x_i = \frac{1}{n} \sum_{i=1}^k n_{i.} \alpha_i = \sum_{i=1}^k f_{i.} \alpha_i$$

De même, pour $Y$, on a observé les classes $\beta_1, \dots, \beta_l$ avec les effectifs respectifs $n_{.1}, \dots, n_{.l}$ :

$$\bar{y} = \frac{1}{n} \sum_{i=1}^n y_i = \frac{1}{n} \sum_{j=1}^l n_{.j} \beta_j = \sum_{j=1}^l f_{.j} \beta_j$$

## Variances marginales

Les variances $\mathbb{V}(x)$ et $\mathbb{V}(y)$ de $X$ et $Y$ sont données par

$$\begin{aligned} \mathbb{V}(x) &= \frac{1}{n} \sum_{i=1}^n (x_i - \bar{x})^2 \\ &= \frac{1}{n} \sum_{i=1}^k n_{i.} (\alpha_i - \bar{x})^2 \\ &= \left( \sum_{i=1}^k f_{i.} \alpha_i^2 \right) - \bar{x}^2 \end{aligned}$$

$$\begin{aligned} \mathbb{V}(y) &= \frac{1}{n} \sum_{i=1}^n (y_i - \bar{y})^2 \\ &= \frac{1}{n} \sum_{j=1}^l n_{.j} (\beta_j - \bar{y})^2 \\ &= \left( \sum_{j=1}^l f_{.j} \beta_j^2 \right) - \bar{y}^2 \end{aligned}$$

# Remarque

Les distributions marginales d'une série statistique double sont l'analogue empirique des [[Lois marginales]] d'un couple de variables aléatoires. Pour les indicateurs calculés sur les individus ayant une modalité fixée de l'autre caractère, voir [[Distributions conditionnelles]] et [[Moyenne et variance conditionnelles]].

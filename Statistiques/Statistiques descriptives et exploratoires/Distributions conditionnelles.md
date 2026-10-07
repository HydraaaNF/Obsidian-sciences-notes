# Définition

La **distribution conditionnelle** du caractère $X$ associée à la modalité $\beta_j$ du caractère $Y$ est constituée des indicateurs associés aux observations de $X$ parmi les [[Population statistique et caractère|individus]] ayant pour caractère $Y$ la modalité $\beta_j$ fixée ; ces indicateurs se calculent à partir des effectifs conjoints $n_{i,j}$ du [[Tableau de contingence]].

Conditionnellement à $Y = \beta_j$, l'effectif total est $n_{.j}$ et la fréquence de la modalité $\alpha_i$ est donnée par

$$f_{i|j} = \frac{n_{i,j}}{n_{.j}}.$$

La moyenne des observations de $X$ conditionnellement à $Y = \beta_j$ est donnée par

$$\bar{x}_j = \frac{1}{n_{.j}} \sum_{i=1}^k n_{i,j} \alpha_i = \sum_{i=1}^k f_{i|j} \alpha_i.$$

La variance des observations de $X$ conditionnellement à $Y = \beta_j$ est donnée par

$$V(x)_j = \frac{1}{n_{.j}} \sum_{i=1}^k n_{i,j} (\alpha_i - \bar{x}_j)^2 = \left( \sum_{i=1}^k f_{i|j} \alpha_i^2 \right) - (\bar{x}_j)^2.$$

On définit de façon similaire les indicateurs associés aux observations de $Y$ parmi les individus ayant pour caractère $X$ la modalité $\alpha_i$.

# Remarque

La variance conditionnelle se met aussi sous la forme « moyenne des carrés moins carré de la moyenne » : $V(x)_j = \left( \sum_{i=1}^k f_{i|j} \alpha_i^2 \right) - (\bar{x}_j)^2$ ; l'écriture $\left( \sum_{i=1}^k f_{i|j} \alpha_i \right)^2 - (\bar{x}_j)^2$ est une erreur fréquente : le carré porte sur chaque valeur $\alpha_i$, et non sur la somme, comme $\sum_{i=1}^k f_{i|j} \alpha_i = \bar{x}_j$, cette écriture vaut identiquement $0$ (voir [[Théorème de König-Huygens]]).

Pour les indicateurs calculés sur l'ensemble des observations, voir [[Distributions marginales]] ; pour la décomposition de la moyenne et de la variance marginales en moyenne et variance conditionnelles, voir [[Moyenne et variance conditionnelles]] ; pour les fréquences conjointes et marginales du tableau, voir [[Fréquences conjointes, marginales et conditionnelles]] ; pour la notion d'indépendance des caractères, voir [[Indépendance de deux caractères]].

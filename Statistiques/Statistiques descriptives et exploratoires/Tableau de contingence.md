# Définition

Le **tableau de contingence**, ou *tableau à double entrée des effectifs*, rassemble les effectifs conjoints d'une [[Série statistique double]] : les modalités $\alpha_1, \dots, \alpha_k$ du caractère $X$ sont disposées en lignes, les modalités $\beta_1, \dots, \beta_l$ du caractère $Y$ en colonnes, et chaque case $n_{i,j}$ désigne le nombre d'[[Population statistique et caractère|individus]] ayant un caractère $X$ égal à $\alpha_i$ et un caractère $Y$ égal à $\beta_j$.

| | $\beta_1$ | $\cdots$ | $\beta_j$ | $\cdots$ | $\beta_l$ | Totaux |
|---|---|---|---|---|---|---|
| $\alpha_1$ | $n_{1,1}$ | $\cdots$ | $n_{1,j}$ | $\cdots$ | $n_{1,l}$ | $n_{1.}$ |
| $\vdots$ | | | | | | |
| $\alpha_i$ | $n_{i,1}$ | $\cdots$ | $n_{i,j}$ | $\cdots$ | $n_{i,l}$ | $n_{i.}$ |
| $\vdots$ | | | | | | |
| $\alpha_k$ | $n_{k,1}$ | $\cdots$ | $n_{k,j}$ | $\cdots$ | $n_{k,l}$ | $n_{k.}$ |
| Totaux | $n_{.1}$ | $\cdots$ | $n_{.j}$ | $\cdots$ | $n_{.l}$ | $n$ |

Le total $n_{i.}$ correspond au nombre d'individus ayant un caractère $X$ égal à $\alpha_i$ et $n_{.j}$ au nombre d'individus ayant un caractère $Y$ égal à $\beta_j$.

# Interprétation

Le total de ligne $n_{i.}$ est la taille du sous-échantillon de modalité $\alpha_i$ et le total de colonne $n_{.j}$ le nombre d'individus de modalité $\beta_j$ dans l'ensemble de la population.

La ligne $i$ décrit la répartition du caractère $Y$ à l'intérieur de la modalité $\alpha_i$ du caractère $X$ : comparer ces répartitions d'une ligne à l'autre revient à comparer les distributions conditionnelles, ce que formalise le [[Test du chi-deux d'indépendance|test du chi-deux d'indépendance]]. Le même tableau, lu en colonnes, sert au [[Test du chi-deux d'homogénéité de plusieurs sous-échantillons|test du chi-deux d'homogénéité de plusieurs sous-échantillons]], où les lignes portent des sous-échantillons d'une même variable.

Le tableau ne contient que des effectifs ; les fréquences s'en déduisent en divisant chaque case par l'effectif total, voir [[Fréquences conjointes, marginales et conditionnelles]].

# Remarque

Le point en indice marque l'indice sur lequel on a sommé :

$$n_{i.} = \sum_j n_{i,j}$$

$$n_{.j} = \sum_i n_{i,j}$$

$$n = \sum_i n_{i.} = \sum_j n_{.j}.$$

Pour les fréquences associées au tableau, voir [[Fréquences conjointes, marginales et conditionnelles]] ; pour les distributions marginales, voir [[Distributions marginales]].

# Définition
Le **support** d'un [[Ensemble flou]] $E$ est l'ensemble classique des éléments qui appartiennent à $E$ **au moins un peu** :

$$
\operatorname{supp}(E) = \{x \in X \mid \mu_E(x) > 0\}
$$

# Propriétés
- Le support est la **coupe de niveau $0$ stricte** : $\operatorname{supp}(E) = E_{\bar{0}}$ (voir [[Coupe de niveau alpha]]).
- Dans le cas classique, $\operatorname{supp}(A) = \operatorname{noyau}(A) = A$.

# Exemple
Pour l'ensemble flou *young* de [[Logique floue]] (égal à $1$ jusqu'à $30$ ans, nul à partir de $45$ ans) : $\operatorname{supp}(\text{young}) = [0, 45[$.

Pour $E = \{1/a,\; 0{,}7/c,\; 0{,}2/e,\; 0{,}3/f,\; 0{,}6/h,\; 0{,}7/j,\; 0{,}9/k\}$ sur $X = \{a, b, \ldots, k\}$ : $\operatorname{supp}(E) = \{a, c, e, f, h, j, k\}$.

# Remarque
À opposer au [[Noyau d'un ensemble flou]], qui rassemble les éléments appartenant **totalement** à $E$.

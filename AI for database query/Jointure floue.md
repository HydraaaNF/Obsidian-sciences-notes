# Définition
Soit $r$ une [[Relation floue]] de schéma $X$, $s$ une relation floue de schéma $Y$, $A$ un sous-ensemble de $X$, $B$ un sous-ensemble de $Y$ et $\theta$ un opérateur de comparaison flou ($<$, $>$, $\leq$, $\geq$, $\neq$, $\ll$, $\gg$, …) :

$$
r \bowtie_{A\,\theta\,B} s = \big\{\mu / \langle u, v \rangle \ \big|\ u \in \operatorname{supp}(r),\ v \in \operatorname{supp}(s),\ \mu = \min\big(\mu_r(u),\ \mu_s(v),\ \mu_\theta(u.A,\ v.B)\big)\big\}
$$

# Propriétés
L'équivalence entre $r \bowtie_{A\,\theta\,B} s$ et $\sigma_{A\,\theta\,B}(r \times s)$ est conservée (voir [[Sélection floue]] et [[Produit cartésien de relations floues]]).

# Remarque
L'égalité approchée est un exemple d'opérateur de comparaison flou : voir [[IN flou]].

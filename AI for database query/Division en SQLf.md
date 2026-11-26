# Définition
En SQLf, aucune des deux solutions SQL de la [[Division en SQL]] (double imbrication, comparaison de cardinalités) ne convient. On utilise l'opérateur $\text{CONTAINS}_{[\text{implication floue}]}$, version floue de l'[[Opérateur CONTAINS]] qui s'appuie sur une [[Implication floue]].

La division $r[A \div B]s$, avec $r$ de schéma $R(X, A)$ et $s$ de schéma $S(Y, B)$, s'écrit :

```sql
SELECT X FROM r GROUP BY X
HAVING set(A) CONTAINS_[implication floue] (SELECT B FROM s)
```

# Interprétation
Pour une valeur $x$ de $X$, $\operatorname{set}(A)$ est l'ensemble des valeurs de $A$ associées à $x$ dans $r$, noté $\Omega_r(x)$ dans la [[Division relationnelle]]. L'opérateur teste l'inclusion de $s[B]$ dans $\Omega_r(x)$ ; son degré est le degré d'[[Inclusion graduelle par une implication floue]], c'est-à-dire la division de relations floues définie dans [[Division de relations floues]].

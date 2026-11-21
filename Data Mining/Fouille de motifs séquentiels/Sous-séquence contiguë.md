#dmv-sequence_mining

# Définition

Soit $w = \langle e_1 \rangle \langle e_2 \rangle \dots \langle e_k \rangle$ une séquence, où chaque $e_i$ est un [[Items, itemsets et base de transactions|itemset]].

Une séquence $s$ est une **sous-séquence contiguë** de $w$ si l'une des conditions suivantes est vérifiée :

- $s$ s'obtient à partir de $w$ en supprimant un item de $e_1$ ou de $e_k$ ;
- $s$ s'obtient à partir de $w$ en supprimant un item de n'importe quel élément $e_i$ contenant au moins deux items ;
- $s$ est une sous-séquence contiguë d'une séquence $s'$, et $s'$ est elle-même une sous-séquence contiguë de $w$ (définition récursive).

# Exemple

La séquence $s = \langle (a)\ (b) \rangle$ est une sous-séquence contiguë de :

- $\langle (a)\ (b\ c) \rangle$ ;
- $\langle (a\ b)\ (b)\ (c) \rangle$ ;
- $\langle (c\ d)\ (a\ b)\ (b\ c)\ (d) \rangle$.

Elle n'est pas une sous-séquence contiguë de :

- $\langle (a)\ (c)\ (b) \rangle$ ;
- $\langle (b)\ (a\ b)\ (c)\ (b) \rangle$.

# Remarque

Les conditions portent sur des suppressions d'items un par un, sans jamais réordonner les éléments ni en fusionner deux : la contiguïté est une exigence plus forte que l'[[Inclusion de sous-séquence|inclusion de sous-séquence]] ordinaire, dont la sous-séquence contiguë est un cas particulier.

Le cas où l'écart entre deux itemsets successifs est nul, $gap = 0$, correspond à cette même exigence de contiguïté dans la [[Contrainte d'écart temporel]] ; c'est ce que prend en compte l'[[Algorithme Gap-BIDE]].

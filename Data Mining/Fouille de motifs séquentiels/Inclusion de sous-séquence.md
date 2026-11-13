#dmv-sequence_mining

# Définition

Soient $S_1 = \langle a_1, \dots, a_n\rangle$ et $S_2 = \langle b_1, \dots, b_m\rangle$ deux séquences.

$S_1$ est une **sous-séquence** de $S_2$, et $S_2$ une **super-séquence** de $S_1$, ce que l'on note $S_1 \subseteq S_2$, s'il existe des entiers $1 \le i_1 < i_2 < \dots < i_n \le m$ tels que :

$$a_1 \subseteq b_{i_1},\ a_2 \subseteq b_{i_2},\ \dots,\ a_n \subseteq b_{i_n}$$

Chaque $a_j \subseteq b_{i_j}$ est l'inclusion ensembliste ordinaire entre deux [[Items, itemsets et base de transactions|itemsets]] : tous les items de $a_j$ figurent dans $b_{i_j}$.

# Exemple

Soit la séquence $S_1 = \langle(10)\ (20\ 30)\ (40)\ (20)\rangle$.

La séquence $S_2 = \langle(20)\ (40)\rangle$ est une sous-séquence de $S_1$ : l'itemset $(20)$ est contenu dans le deuxième élément $(20\ 30)$ et l'itemset $(40)$ dans le troisième élément, avec $2 < 3$.

La séquence $S_3 = \langle(20)\ (30)\rangle$ n'est pas une sous-séquence de $S_1$ : les items $20$ et $30$ apparaissent ensemble dans un même élément de $S_1$, et un élément ne peut pas être scindé pour fournir deux positions distinctes $i_1 < i_2$.

# Remarque

Les positions $i_1, \dots, i_n$ doivent être strictement croissantes, mais pas consécutives : des éléments de $S_2$ peuvent être ignorés entre deux éléments retenus, si bien qu'une sous-séquence n'est pas nécessairement formée d'éléments adjacents. La contrainte d'adjacence définit une notion plus forte, celle de [[Sous-séquence contiguë]].

L'inclusion de sous-séquence est la relation qui compare un [[Motif séquentiel|motif séquentiel]] aux séquences d'une [[Base de séquences|base de séquences]] : c'est elle qui décide de la présence du motif, et donc du [[Support d'un motif séquentiel|support]] qui lui est attribué.

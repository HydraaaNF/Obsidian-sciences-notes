# Définition

Un **treillis** (trellis) peut être vu comme une matrice (ou un graphe) dont les éléments sont des couples (état, observation). L'une des dimensions correspond aux observations $o_1, \ldots, o_T$ et l'autre aux états de la [[Chaîne de Markov à temps discret|chaîne de Markov]].

Chaque élément du treillis possède un ensemble de **prédécesseurs** définis par la topologie de la chaîne de Markov : les éléments de l'observation précédente dont l'état admet une transition vers l'état de l'élément considéré.

Un **chemin** dans le treillis est une séquence d'états $S_1, \ldots, S_T$ (un état par observation) où chaque transition entre états consécutifs est une transition possible de la chaîne.

# Exemple

Deux chemins dans un treillis à quatre états et huit observations $o_1, \ldots, o_8$ :

- $S_1 = 1$, $S_2 = 1$, $S_3 = 2$, $S_4 = 3$, $S_5 = 3$, $S_6 = 4$, $S_7 = 4$, $S_8 = 4$ ;
- $S_1 = 2$, $S_2 = 2$, $S_3 = 2$, $S_4 = 2$, $S_5 = 2$, $S_6 = 3$, $S_7 = 3$, $S_8 = 4$.

Sur le treillis, chaque chemin traverse un élément (état, observation) par observation ; les séquences ci-dessus se lisent donc comme des trajectoires colonne par colonne, où A désigne le premier chemin et B le second :

| État | $o_1$ | $o_2$ | $o_3$ | $o_4$ | $o_5$ | $o_6$ | $o_7$ | $o_8$ |
|---|---|---|---|---|---|---|---|---|
| 4 | | | | | | A | A | A B |
| 3 | | | | A | A | B | B | |
| 2 | B | B | A B | B | B | | | |
| 1 | A | A | | | | | | |

# Remarque

Le treillis est la structure d'implémentation de l'[[Algorithme de Viterbi]] ; l'[[Algorithme forward]] et l'[[Algorithme backward]] s'appuient sur la même structure.

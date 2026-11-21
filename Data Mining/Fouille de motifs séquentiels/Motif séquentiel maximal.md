#dmv-sequence_mining

# Définition

Un **motif séquentiel maximal** sur un ensemble de motifs $S$ est un motif $s \in S$ qu'aucun motif de $S$ ne contient strictement :

$$\forall s' \in S,\ s \not\subsetneq s'$$

Autrement dit, il n'existe pas de $s' \in S$ tel que $s \subsetneq s'$. La comparaison est celle de l'[[Inclusion de sous-séquence]], et le [[Support d'un motif séquentiel|support]] n'intervient pas dans la condition.

# Exemple

Six [[Motif séquentiel|motifs séquentiels]] et leurs supports, à classer comme maximaux ou non :

| Motif | Support | Maximal ? | Clos ? |
| :-- | :-- | :-- | :-- |
| $\langle(a\ b)(c)(e)\rangle$ | 2 | oui | oui |
| $\langle(a)(c)(d)\rangle$ | 4 | oui | oui |
| $\langle(a)(c)(e)\rangle$ | 3 | non | oui |
| $\langle(c)(d)(e)\rangle$ | 5 | oui | oui |
| $\langle(a)(c)\rangle$ | 4 | non | non |
| $\langle(b)\rangle$ | 7 | non | oui |

Les réponses se lisent sur les seules relations d'inclusion entre ces six motifs :

- $\langle(a)(c)\rangle$ est contenu dans $\langle(a)(c)(d)\rangle$, qui a le même support : il n'est ni maximal ni clos ;
- $\langle(b)\rangle$ est contenu dans $\langle(a\ b)(c)(e)\rangle$ : son support plus élevé le laisse clos sans le rendre maximal ;
- $\langle(a)(c)(e)\rangle$ est contenu dans $\langle(a\ b)(c)(e)\rangle$ : il reste clos, le motif plus long ayant un support strictement plus faible ;
- $\langle(a\ b)(c)(e)\rangle$, $\langle(a)(c)(d)\rangle$ et $\langle(c)(d)(e)\rangle$ ne sont contenus dans aucun autre motif de la liste : ce sont les trois motifs maximaux.

# Remarque

L'inclusion de la définition est stricte : un motif est toujours contenu dans lui-même, et une inclusion non stricte disqualifierait tout motif de $S$.

Un motif maximal est toujours clos : s'il n'admet aucun sur-motif dans $S$, il n'en admet a fortiori aucun de même support, condition qui définit les [[Motif séquentiel clos|motifs clos]]. La réciproque est fausse, comme le montre l'exemple, où $\langle(b)\rangle$ et $\langle(a)(c)(e)\rangle$ sont clos sans être maximaux.

Deux motifs maximaux distincts ne sont jamais emboîtés : si $s \subsetneq s'$ avec $s, s' \in S$, c'est $s'$ qui interdit à $s$ d'être maximal. Les motifs maximaux de $S$ sont donc deux à deux incomparables, et un motif maximal cesse de l'être dès qu'un sur-motif lui est ajouté dans $S$.

La notion est l'analogue, pour les séquences, de l'[[Itemsets fréquents maximaux|itemset fréquent maximal]] : la maximalité s'y entend sur des suites ordonnées d'itemsets, et non sur des ensembles d'items.

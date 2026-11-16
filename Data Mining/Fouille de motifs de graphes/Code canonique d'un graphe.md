#dmv-graph_mining

# Définition

Un code canonique associe à chaque graphe un code, c'est-à-dire une représentation à une dimension d'un objet qui en compte deux :
- à chaque graphe on associe un code, de telle sorte que deux graphes de codes égaux soient isomorphes ;
- le plus petit code possible d'un graphe, pour l'ordre choisi sur les codes, est son code canonique.

# Propriétés

- Deux graphes ont le même code canonique si et seulement s'ils sont isomorphes.
- Le code canonique identifie un graphe de façon unique.

# Interprétation

Un même motif peut être atteint par plusieurs chemins de recherche : des extensions ou des fusions différentes produisent des graphes isomorphes, donc un même motif. Sans précaution, la fouille génère plusieurs fois le même motif.

Deux parades existent :

- imposer une stratégie de génération qui limite les doublons, par exemple toujours étendre à partir du dernier sommet développé, comme le font MoFa et gSpan ; cette stratégie ne suffit pas à elle seule, puisque deux chaînes d'extensions distinctes peuvent encore converger vers le même motif ;
- détecter qu'un motif peut être obtenu par un autre chemin de recherche. L'approche naïve, qui compare le motif à tous ceux déjà générés, est exclue en temps de calcul comme en mémoire ; les codes canoniques, employés par gSpan, FFSM et Gaston, la remplacent.

Dans la génération, on n'étend un motif que sur les chemins de recherche qui produisent son code canonique. C'est la base de l'[[Élagage par codes canoniques]].

# Remarque

Le code maximal conviendrait aussi bien que le code minimal, le choix est arbitraire. Le minimum se calcule relativement à un ordre sur les codes : avec les codes en profondeur d'abord du [[Code DFS d'un graphe]], cet ordre est l'ordre lexicographique des éléments du code, décrit dans l'[[Ordre et code DFS minimal]].

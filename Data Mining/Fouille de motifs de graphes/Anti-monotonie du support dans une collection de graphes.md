#dmv-graph_mining

# Propriétés

Le support est anti-monotone par rapport à la relation de sous-graphe : le support d'un graphe est inférieur ou égal au support de ses sous-graphes.

Pour deux motifs $P$ et $P'$ tels que $P$ soit un sous-graphe isomorphe de $P'$ :

$$\text{Support}(P') \le \text{Support}(P)$$

### Démonstration

Tout graphe de la collection qui contient $P'$ contient aussi $P$, puisque $P$ est un sous-graphe de $P'$ : l'ensemble des graphes comptés pour $P'$ est donc inclus dans celui compté pour $P$. L'inclusion des ensembles donne l'inégalité des cardinaux, et le dénominateur $|D|$ est commun aux deux motifs.

# Remarque

La propriété s'énonce aussi par contraposée sur la fréquence : si un motif n'est pas fréquent, aucun de ses sur-graphes ne l'est. Un motif trop rare ferme donc d'un bloc toute la branche de ses extensions, ce qui permet d'élaguer la recherche au lieu de calculer le support de chaque candidat.

Elle repose entièrement sur la règle de contribution unique d'un graphe au [[Support d'un motif dans une collection de graphes|support]] : c'est cette règle qui garantit l'inclusion des ensembles de graphes comptés. Une mesure qui compte chaque occurrence à l'intérieur d'un graphe, comme le [[Support naïf par comptage d'occurrences]], la perd, et les mesures qui gèrent le chevauchement des occurrences, comme le [[Support par chevauchement]], doivent être examinées séparément avant d'en tirer un élagage.

Un motif ne peut donc avoir un support supérieur à celui d'un de ses sous-graphes, mais rien n'interdit à deux motifs incomparables d'avoir des supports très différents.

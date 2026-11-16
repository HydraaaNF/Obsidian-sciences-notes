#dmv-graph_mining

# Définition

La fouille de motifs de graphes est le problème de découvrir les sous-graphes fréquents, appelés motifs, présents dans le ou les graphes de données en entrée.

# Interprétation

Les données de graphes sont disponibles en grande quantité : réseaux physiques (télécommunications), réseaux sociaux, molécules, graphes d'appels de programmes, web sémantique.

L'intérêt est de découvrir des motifs de sous-graphes dans ces données :

- trouver des structures décrivant des concepts intéressants
- abstraire des parties des données comme instances de motifs
- apprendre sur les données en regardant ce qui y est fréquent

La fouille de motifs de graphes étend aux graphes l'[[Extension de la fouille de motifs aux données structurées|extension de la fouille de motifs aux données structurées]] : le motif n'y est plus un ensemble d'éléments mais un sous-graphe, dont l'occurrence se teste par [[Isomorphisme de sous-graphe|isomorphisme de sous-graphe]].

# Remarque

Compter les occurrences d'un motif et décider de sa fréquence demande une mesure de [[Support d'un motif de graphe|support]].

L'énumération des motifs fréquents se fait par [[Algorithmes par fusion de motifs|fusion de motifs]] ou par [[Croissance de motifs de graphes|croissance de motifs]].

Le déroulement complet de la fouille, du jeu de données aux motifs retenus, est résumé dans [[Illustration et bilan de la fouille de motifs de graphes]].

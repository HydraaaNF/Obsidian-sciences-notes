#dmv-subgroup_discovery

# Définition

La recherche des sous-groupes est le parcours de l'ensemble des [[Motif de sous-groupe|motifs de sous-groupe]] obtenus en ajoutant un [[Sélecteur d'un motif de sous-groupe|sélecteur]] à un motif déjà construit, en partant du motif vide qui couvre la population entière.

Elle se mène de deux façons : le parcours exhaustif, qui visite tout l'[[Espace de recherche des sous-groupes|espace de recherche]] compatible avec les contraintes posées, et la recherche heuristique, qui n'en visite qu'une partie choisie d'après la [[Fonction de qualité d'un sous-groupe|qualité]] des candidats.

# Modèle

L'espace parcouru est l'arbre de raffinements décrit dans [[Espace de recherche des sous-groupes]] : sa racine, ses nœuds, sa profondeur et l'élagage des motifs réengendrés y sont définis et ne sont pas repris ici.

La recherche n'ajoute à cet espace que la façon de le visiter.

- Le parcours exhaustif le visite en profondeur d'abord : un motif est raffiné jusqu'à ses descendants les plus spécifiques avant que ses frères ne soient examinés.
- La recherche heuristique n'ouvre à chaque niveau qu'une partie des branches, choisie d'après la qualité de leurs motifs.

# Algorithme

## Parcours exhaustif

Le parcours exhaustif combine trois éléments.

- Une exploration en profondeur d'abord, comme dans la [[Recherche en profondeur d'Eclat|recherche en profondeur d'Eclat]].
- Des structures de données efficaces, du type de l'[[Arbre FP]].
- Un élagage des branches, le plus souvent l'[[Élagage top-k]], qui repose sur une [[Estimation optimiste d'une fonction de qualité|estimation optimiste]] de la qualité.

Trois algorithmes en sont représentatifs.

- SD-Map (Atzmueller et Puppe, 2006)
- SD-Map* (Atzmueller et Lemmerich, 2009)
- Merge-SD (Grosskreutz et Rueping, 2009)

## Recherche heuristique

La recherche heuristique remplace le parcours complet par une exploration guidée par la qualité.

- Elle est le plus souvent une recherche en faisceau, dont la [[Recherche en faisceau diversifiée]] est la variante guidée par la diversité.
- Des travaux récents y emploient une recherche arborescente de Monte-Carlo (MCTS, pour Monte-Carlo Tree Search).

# Interprétation

Le faisceau se lit directement sur le treillis des motifs : il n'ouvre à chaque niveau qu'une bande étroite de candidats, celle des meilleurs, et cette bande descend du sommet vers les motifs spécifiques.

Deux effets en découlent.

- Les motifs de bonne qualité situés hors de la bande, qui sont des optima locaux, ne sont jamais atteints, puisque leurs ancêtres n'ont pas été retenus.
- Le seuil de support minimal coupe le bas du treillis : les motifs trop spécifiques, qui ne couvrent plus assez d'individus, sont hors d'atteinte quelle que soit leur qualité.

La recherche arborescente de Monte-Carlo procède autrement : les régions qu'elle visite forment plusieurs taches disjointes dans le treillis plutôt qu'une bande continue.

# Remarque

Le parcours exhaustif et la recherche heuristique ne diffèrent que par l'étendue de l'exploration, pas par la mesure employée : dans les deux cas, un candidat est jugé par sa [[Fonction de qualité d'un sous-groupe|fonction de qualité]] sur la population qu'il couvre.

Le parcours exhaustif échange du temps de calcul contre la complétude de la visite ; l'[[Élagage top-k]] en réduit le coût, et l'[[Estimation optimiste d'une fonction de qualité|estimation optimiste]] sur laquelle il repose est traitée dans sa propre note. La recherche heuristique échange la complétude contre le coût : elle atteint des motifs profonds en peu d'évaluations, au prix des optima locaux qu'elle laisse hors de sa bande.

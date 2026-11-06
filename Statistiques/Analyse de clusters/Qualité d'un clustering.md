# Propriétés

L'évaluation de la qualité d'un [[Clustering|clustering]] est une question difficile ; plusieurs critères peuvent être retenus :

- l'**évaluation subjective**, par inspection des clusters ;
- la **distorsion intra-cluster**, si une métrique significative existe : c'est la quantité minimisée par le [[k-means]], son inertie :

$$\sum_k \sum_{x \in S_k} \lVert x - c_k \rVert^2$$

où $S_k$ désigne l'ensemble des points du cluster $k$ et $c_k$ son centre ;
- tout **critère objectif de qualité choisi arbitrairement**, mais aucun critère prêt à l'emploi ;
- le **cas particulier des [[Clustering ascendant pour le partitionnement temporel|segmentations temporelles]]**.

# Interprétation

L'appréciation des clusters obtenus est donc largement subjective, par inspection ; une mesure quantitative n'est disponible que si une métrique significative existe, par exemple la distorsion intra-cluster, et tout critère objectif restant relève d'un choix arbitraire.

Le cas particulier des segmentations temporelles s'illustre par un [[Clustering hiérarchique|dendrogramme]] de segments temporels : une coupe (trait pointillé) le traverse et délimite trois groupes de segments, repris sur la frise au-dessous en trois couleurs (rouge, vert et bleu) ; sous la frise, quatre cases étiquetées A, B, C, A.

# Remarque

Voir aussi le [[Choix d'une méthode de clustering|choix d'une méthode de clustering]] et le [[Choix du nombre de clusters|choix du nombre de clusters]].

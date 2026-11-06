# Définition

**DBSCAN** (*Density-Based Spatial Clustering of Applications with Noise*) est un algorithme de [[Clustering par densité|clustering par densité]]. Il repose sur la [[Points core, border et noise|classification des points]] en core, border et noise, puis sur l'exploration d'un graphe de voisinage construit à partir d'une [[Mesures de similarité et de distance|mesure de distance]]. Il repère les points densément connectés par analyse de voisinage, permet des clusters de forme arbitraire et s'exécute en un seul passage sur les données.

# Algorithme

L'algorithme procède en trois étapes :

1. **étiqueter les points et construire le graphe** ;
2. **chercher les composantes connexes** ;
3. **étiqueter les points border**.

La recherche des composantes connexes s'effectue tant qu'il reste des points non étiquetés :

1. choisir un point non étiqueté et lui attribuer une nouvelle étiquette ;
2. identifier sa composante grâce à un parcours DFS ou BFS.

# Interprétation

Chaque point est d'abord étiqueté (core, border ou noise) et relié à ses voisins dans un graphe ; la recherche des composantes connexes de ce graphe fait apparaître les clusters. Le principe se résume en quatre temps :

1. étiqueter les points ;
2. éliminer les points noise ;
3. créer les clusters à partir des points core ;
4. affecter les points border aux clusters de points core.

# Exemple

Sur un jeu de données en deux dimensions formant deux amas recourbés, le déroulé est le suivant : les points bruts ; puis les points étiquetés et reliés à leurs voisins dans un graphe, les points isolés (noise) restant à l'écart ; puis les composantes connexes du graphe, qui forment deux clusters distincts ; enfin le rattachement des points border à ces clusters.

# Remarque

La classification des points en core, border et noise et les deux paramètres associés (rayon de voisinage et nombre minimal de points) sont détaillés dans [[Points core, border et noise]]. Les avantages et inconvénients de DBSCAN sont traités dans [[Avantages et inconvénients de DBSCAN]].

DBSCAN est l'algorithme le plus connu de sa famille, mais d'autres méthodes par densité existent, notamment **OPTICS** (variante gérant mieux des densités variables) et **DENCLUE** (approche fondée sur l'[[Lissage d'histogramme|estimation de densité par noyau]]).

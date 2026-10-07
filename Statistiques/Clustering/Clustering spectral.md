# Définition

Le **clustering spectral** est une méthode de [[Clustering|clustering]] qui représente les données sous forme de graphe : chaque point de données est un nœud du graphe, et les arêtes encodent la similarité entre deux nœuds avec des poids $w_{ij}$, donnés par une [[Mesures de similarité et de distance|mesure de similarité ou de distance]].

Trois familles de graphes de similarité se distinguent :

- les **graphes de $\varepsilon$-voisinage**, où deux points sont reliés lorsque leur distance est inférieure à $\varepsilon$ ;
- les **graphes des $k$ plus proches voisins**, où chaque point est relié à ses $k$ plus proches voisins ;
- les **graphes complètement connectés**, où chaque paire de points est reliée.

# Exemple

Un même échantillon de points illustre la construction du graphe de similarité : nuage de points seul, graphe de $\varepsilon$-voisinage ($\varepsilon = 0{,}3$), graphe des $k$ plus proches voisins ($k = 5$) et sa variante mutuelle.

**Exemple jouet.** Sur un échantillon de points, l'exemple jouet présente l'histogramme de l'échantillon, les valeurs propres et les cinq premiers vecteurs propres de plusieurs variantes, normalisées ou non, du [[Laplacien du graphe]] ; la plus petite valeur propre non nulle est strictement positive ($\nu_1 > 0$).

# Remarque

Le graphe de similarité est la structure exploitée par le [[Laplacien du graphe]], puis par l'[[Algorithme de clustering spectral]].

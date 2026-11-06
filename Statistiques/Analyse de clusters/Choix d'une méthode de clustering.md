# Interprétation

Pour choisir la méthode de [[Clustering|clustering]] la plus appropriée parmi les [[Types de clustering|types de clustering]], il faut examiner les éléments suivants :

- le **type de mesure de proximité ou de densité** : la forme de la [[Mesures de similarité et de distance|mesure de similarité ou de distance]] entre les objets ;
- la **rareté** (*sparseness*) : elle dicte le type de similarité et améliore l'efficacité ;
- le **type d'attributs** : il dicte le type de similarité ;
- le **type de données** ;
- la **dimensionnalité** (voir [[Clustering en grande dimension]]) ;
- le **bruit et les points aberrants** ;
- le **type de distribution** des données.

# Exemple

Une comparaison de plusieurs algorithmes de clustering sur des jeux de données de formes variées illustre la dépendance du résultat au choix de la méthode. Chaque ligne correspond à un jeu de données : anneaux concentriques bruités, demi-lunes bruitées, amas de tailles et de densités inégales, amas allongés, données sans structure apparente. Chaque colonne correspond à un algorithme : [[k-means|k-means par mini-lots]], propagation d'affinité, MeanShift, [[Clustering spectral|clustering spectral]], méthode de Ward, [[Clustering agglomératif et divisif|clustering agglomératif]], [[DBSCAN]], OPTICS, Birch et mélange gaussien.

Pour un même jeu de données, les partitions obtenues diffèrent fortement d'un algorithme à l'autre : certaines méthodes suivent les structures des nuages (anneaux concentriques, demi-lunes), tandis que d'autres les découpent en groupes qui ne suivent pas ces formes ; sur plusieurs jeux de données, DBSCAN et OPTICS isolent une partie des points comme bruit (affichés en noir) au lieu de les rattacher à un cluster. Le temps d'exécution, indiqué sous chaque résultat, varie lui aussi fortement d'un algorithme à l'autre.

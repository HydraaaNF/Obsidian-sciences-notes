# Propriétés

- **Distance** : la distance est l'élément clé du [[k-means]], la moyenne doit avoir un sens pour la mesure choisie. Sinon, on peut utiliser la médiane à la place (algorithmes des k-medians ou k-medoids).
- **Convergence** : elle est garantie (plus rien ne bouge) et survient souvent en 10 à 20 itérations ; l'[[Algorithme des k-moyennes de Lloyd|algorithme des k-moyennes]] s'arrête donc toujours.
- **Complexité** : $O(iKNd)$, avec $i = \#\text{itérations}$ et $d = \text{dimension}(x_i)$, $K$ le nombre de clusters (voir [[Choix du nombre de clusters]]) et $N$ le nombre d'exemples.

# Remarque

L'initialisation est délicate :
- le choix initial des centroïdes est **aléatoire** ;
- on peut lancer l'algorithme **plusieurs fois**, mais cela coûte cher, et il faut alors gérer les clusters « morts », par exemple en les remplaçant ;
- le [[k-means hiérarchique de Linde-Buzo-Gray]] (aussi appelé bisecting k-means) fournit une initialisation hiérarchique qui corrige la dépendance au choix aléatoire des centroïdes.

En tout cas, le k-means ne garantit que des **optima locaux** : un mauvais départ peut mener à un mauvais découpage définitif (voir [[Avantages et inconvénients du k-means]]).

L'écriture « k-medioids » est une coquille : la forme usuelle est k-medoids : le nom vient de medoid, l'objet d'un cluster dont la dissimilarité moyenne aux autres points est minimale.

# Exemple

Un jeu de données en deux dimensions, exécuté avec deux initialisations différentes, illustre le poids du choix des centroïdes de départ.

**Initialisation favorable** : les points forment trois groupes nettement séparés, un en haut, un en bas à gauche, un en bas à droite. À l'itération 6, chacun des trois centroïdes s'est placé au cœur de son groupe et les clusters obtenus épousent les trois groupes naturels, à quelques points isolés près.

**Initialisation défavorable** : deux des centroïdes initiaux tombent dans la partie supérieure du nuage et le troisième entre les deux groupes du bas. Des itérations 1 à 5, la configuration ne se débloque pas : le groupe du haut reste scindé en deux clusters tandis que les deux groupes du bas restent réunis dans un même cluster, dont le centroïde demeure dans la zone vide qui les sépare. L'algorithme converge vers un optimum local.

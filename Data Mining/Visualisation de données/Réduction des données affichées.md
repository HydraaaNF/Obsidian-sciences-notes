#dmv-visualization

# Définition

**Reduce** regroupe trois opérations qui diminuent la quantité de données représentée dans la vue :

- Filter : retirer des données et ne conserver qu'un sous-ensemble ;
- Aggregate : remplacer un ensemble de valeurs par un résumé ;
- Embed : intégrer une vue à l'intérieur d'une marque de la vue principale.

# Exemple

Trois familles de représentations illustrent ces opérations :

- la boîte à moustaches et le diagramme en violon, qui résument la distribution d'une variable pour chaque catégorie en quelques paramètres ou en une silhouette de densité ;
- le nuage de points continu, où la densité des points est encodée par la couleur sur les deux attributs continus ;
- une projection MDS d'un nuage de points de grande dimension, qui replace les observations en deux dimensions à partir de leurs dissimilarités.

L'intégration d'une vue dans une marque est illustrée par des lentilles magiques posées sur un graphique de flux : la lentille affiche en surimpression un détail de la zone qu'elle recouvre.

# Interprétation

Les trois opérations réduisent la quantité affichée par des moyens différents : le filtre agit sur les données elles-mêmes, l'agrégation sur leur résumé, l'intégration sur la place de la vue secondaire dans la vue principale.

# Remarque

La lentille magique de l'exemple est posée sur le graphique de flux des prénoms décrit dans [[Graphique de flux]].

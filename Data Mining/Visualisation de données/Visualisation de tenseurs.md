#dmv-visualization

# Définition

La visualisation de tenseurs représente un champ de tenseurs d'ordre 2, c'est-à-dire une valeur tensorielle attachée à chaque point d'un domaine spatial. Chaque point est résumé par un glyphe dont la géométrie encode les éléments propres du tenseur : les valeurs propres fixent les dimensions du glyphe, les vecteurs propres son orientation.

Deux familles de glyphes servent à cette représentation :

- les ellipsoïdes, dont les demi-axes portent les valeurs propres et dont l'axe long suit la direction propre principale ;
- les superquadriques, obtenues en déformant une sphère vers des formes à arêtes, bâtonnets ou boîtes, dont les arêtes marquent les directions propres.

# Interprétation

L'ellipsoïde donne une forme lisse : l'orientation se lit dans l'aplatissement et l'allongement du volume. La superquadrique donne une forme anguleuse : les arêtes et les faces rendent les directions plus franches, au prix d'une lecture moins immédiate de la magnitude.

Les deux représentations s'appliquent au même champ : ce sont deux encodages concurrents du même tenseur, que l'on compare en densité et en lisibilité.

# Remarque

Un champ de tenseurs est un cas particulier de champ continu, l'un des [[Types de jeux de données]] : la grille de positions y est celle du domaine, et la valeur de chaque cellule un tenseur plutôt qu'un scalaire.

Ce type de représentation relève de la [[Visualisation scientifique et visualisation d'information|visualisation scientifique]], qui traite les données spatiales discrétisées. Le glyphe n'est qu'un des canaux possibles pour une valeur multidimensionnelle, à comparer aux autres [[Canaux visuels et efficacité d'encodage]].

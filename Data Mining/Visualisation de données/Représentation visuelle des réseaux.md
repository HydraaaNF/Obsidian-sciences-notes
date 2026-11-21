#dmv-visualization

# Définition

Un réseau est un [[Types de jeux de données|jeu de données]] fait de nœuds et de liens. Le même réseau admet plusieurs représentations visuelles, qui ne montrent pas les mêmes propriétés :

- la matrice d'adjacence : une cellule par paire de nœuds, marquée quand un lien existe ; un ordre groupé des lignes et des colonnes fait apparaître des blocs et laisse lire la diagonale
- la disposition circulaire : les nœuds sont placés sur un cercle et chaque lien est tracé comme une corde intérieure
- la disposition nœuds-liens : les nœuds sont posés librement, les liens tracés comme des segments, selon un algorithme de placement guidé par les forces

# Interprétation

Le choix entre ces tracés arbitre entre lisibilité globale et lisibilité locale :

- la matrice montre sans ambiguïté l'absence ou la présence d'un lien, mais un nœud très connecté y devient une ligne entière de marques
- la disposition circulaire rend chaque nœud atteignable, au prix d'un enchevêtrement de cordes dès que le réseau est dense
- la disposition nœuds-liens fait apparaître les groupes et les positions relatives, mais noie les liens dans les zones denses et varie d'un calcul à l'autre

La couleur des nœuds, ou les bandes colorées le long des axes de la matrice, servent à porter une partition du réseau, ce qui rapproche ces vues de la lecture multi-vue décrite dans [[Vues multiples coordonnées]].

# Exemple

Dépendances entre les classes d'une hiérarchie logicielle, tracées en arcs radiaux : les classes sont disposées sur un cercle selon leur place dans la hiérarchie, et les dépendances empruntent des faisceaux d'arcs qui se regroupent le long du chemin hiérarchique partagé. Les grands paquets de dépendances se lisent à l'épaisseur et à la couleur des faisceaux.

Un même réseau de cooccurrences, coloré par groupes de nœuds, se lit indifféremment en matrice d'adjacence ordonnée, en cercle et en nœuds-liens : les blocs de la matrice correspondent aux amas de la disposition nœuds-liens.

# Remarque

Le tracé en arcs radiaux groupés est un faisceau d'arêtes hiérarchique, et non un diagramme de cordes : le nommer diagramme de cordes est une confusion fréquente. Un diagramme de cordes représente des flux entre entités par des cordes dont l'épaisseur code le volume échangé, alors que le faisceau d'arêtes ne fait que relier des entités par leur appartenance à une même branche d'une hiérarchie.

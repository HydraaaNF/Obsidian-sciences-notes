#dmv-visualization

# Définition

Facetter une visualisation consiste à répartir les données entre plusieurs vues au lieu de tout montrer dans une seule, selon trois modes :

- juxtaposer : les vues sont placées côte à côte, chacune portant une partie des données
- partitionner : une même vue est découpée en sous-vues, par exemple selon une variable de découpage
- superposer : les vues sont dessinées l'une sur l'autre dans un même cadre

# Interprétation

Le motif de référence est la combinaison d'une vue d'ensemble et de vues de détail : l'ensemble situe, le détail précise, et l'utilisateur passe de l'un à l'autre sans perdre le contexte.

Les vues restent coordonnées : une sélection opérée dans l'une se répercute dans les autres, ce qui permet de suivre un même enregistrement d'une représentation à l'autre. C'est ce qui distingue un ensemble de vues coordonnées d'une simple collection de figures, et ce qui les rend complémentaires de la [[Manipulation d'une visualisation|manipulation]] et des techniques de [[Réduction des données affichées|réduction]].

# Exemple

Voyager 2 présente un jeu de données de voitures en vues multiples coordonnées, un panneau par attribut :

- diagrammes en barres du nombre de voitures par nombre de cylindres, par nom de modèle et par origine
- courbe du nombre de voitures par année
- histogrammes des valeurs regroupées en classes pour l'accélération, la cylindrée, la puissance et la consommation

Les panneaux se répondent : un même enregistrement se retrouve d'une vue à l'autre, si bien que la description d'un sous-ensemble se lit simultanément sur tous les attributs.

Une matrice d'adjacence et un tracé nœuds-liens du même réseau peuvent de la même façon être juxtaposés, voir [[Représentation visuelle des réseaux]].

# Remarque

Le facettage est l'une des réponses de la famille des questions du comment, après l'arrangement, l'encodage et la manipulation : voir [[Questions du comment en conception de visualisation]]. Il multiplie les vues, donc le coût d'attention, ce qui renvoie aux [[Limites de la perception humaine|limites de la perception humaine]].

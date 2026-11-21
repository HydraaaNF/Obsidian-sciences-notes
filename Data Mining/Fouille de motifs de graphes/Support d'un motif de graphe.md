#dmv-graph_mining

# Définition

La découverte de sous-graphes fréquents consiste à découvrir les sous-graphes dont le support atteint ou dépasse un seuil minimal fixé par l'utilisateur :

$$\text{support}(P) \ge \text{minsup}$$

Un sous-graphe qui atteint ce seuil est un motif fréquent de graphe.

# Remarque

L'idée de base reste celle des autres domaines de fouille de motifs : combien de fois le motif apparaît-il dans les données d'entrée ?

Seule la définition précise du support dépend du type de données graphe, et c'est là que les mesures divergent :

- sur un graphe unique, les occurrences se comptent dans le graphe lui-même, avec le [[Support naïf par comptage d'occurrences]], le [[Support par chevauchement]] ou le [[Support par image minimale]].

Ces mesures répondent toutes à la même question, mais leurs valeurs ne se comparent pas : une proportion de graphes et un nombre d'occurrences dans un graphe ne désignent pas la même quantité, et le seuil $minsup$ s'exprime dans l'unité de la mesure retenue.

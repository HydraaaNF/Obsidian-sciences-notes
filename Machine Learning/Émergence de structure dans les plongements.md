#ml-3

# Interprétation

Un [[Plongement|plongement]] ne sert pas qu'à alimenter les couches suivantes : la position de ses vecteurs dans l'espace est elle-même informative. Pour la lire, on projette les plongements d'entrée sur leurs deux premières composantes principales, c'est-à-dire sur le plan qui conserve le mieux les distances entre symboles (voir l'[[Analyse en composantes principales]]).

La **structure** désigne l'organisation d'ensemble de ces positions : des symboles rassemblés par affinité, des voisinages réguliers, une disposition reconnaissable. Un nuage de points sans ordre n'en porte aucune, quelle que soit la performance du modèle.

L'observation centrale est que la généralisation coïncide avec l'apparition de cette structure : le modèle ne prédit correctement des données qu'il n'a jamais vues qu'au moment où les plongements s'organisent.

# Exemple

Un [[Architecture du Transformer|Transformer]] apprend l'addition modulaire. Le plan des deux premières composantes principales de ses plongements d'entrée est relevé à trois stades de l'entraînement :

| Stade | Itérations | Exactitude entraînement | Exactitude validation | Plongements d'entrée |
| --- | --- | --- | --- | --- |
| Initialisation | 0 | 0,0 | 0,0 | nuage dispersé, sans voisinage |
| Surapprentissage | 1000 | 1,0 | 0,1 | nuage étalé, voisinages mêlés |
| Apprentissage de représentation | 20000 | 1,0 | 1,0 | anneau ordonné, numéros consécutifs voisins |

À l'initialisation, les points sont éparpillés au hasard et le modèle ne réussit sur rien.

Après 1000 itérations, l'exactitude d'entraînement est parfaite mais celle de validation reste à 0,1 : le modèle a appris les exemples sans généraliser, et les plongements forment encore un nuage étalé, où les points proches ne partagent aucun ordre.

Après 20000 itérations, les deux exactitudes valent 1,0 et les points se disposent sur un anneau : deux points voisins portent des numéros consécutifs, les numéros se succèdent sur tout le tour de l'anneau, et la couleur des points change progressivement le long de cet anneau.

# Remarque

L'exactitude d'entraînement ne dit rien de la représentation : elle atteint déjà 1,0 au stade où la validation plafonne à 0,1, ce qui est la signature du [[Surapprentissage et sous-apprentissage|surapprentissage]]. La structure des plongements est donc un diagnostic plus direct que la seule performance.

Les vecteurs observés sont les lignes de la table apprise par la [[Couche de plongement]] : c'est cette table que l'entraînement organise, et non un dispositif ajouté après coup.

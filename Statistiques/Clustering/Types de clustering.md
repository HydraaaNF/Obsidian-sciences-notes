# Définition

Le [[Clustering|clustering]] conduit à un ensemble de clusters. Deux façons d'organiser les données se distinguent :

- **le partitionnement** : diviser l'ensemble des données en clusters non chevauchants, chaque objet appartenant à un seul et unique cluster ;
- **l'agrégation** : regrouper des données similaires en clusters imbriqués, formant une structure hiérarchique : voir [[Clustering hiérarchique]].

D'autres philosophies existent : l'[[Clustering par densité|approche par densité]] (density-based), l'approche par grille (grid-based), l'approche par modèle (model-based), l'approche par contraintes (constraints-based), etc.

Les types de clustering se distinguent également par plusieurs caractéristiques :

- **exclusif ou non ?** les points peuvent appartenir à plusieurs clusters (avec ou sans poids) ;
- **flou (fuzzy) ou non ?** dans un algorithme flou, un point appartient à tous les clusters avec un poids $\in [0, 1]$ ;
- **partiel ou non ?** seule une partie des données est regroupée en clusters ;
- **homogène ou non ?** les clusters peuvent être de forme très différente.

Pour le choix d'une méthode de clustering, voir [[Choix d'une méthode de clustering]].

# Interprétation

Sur une représentation plane des données, les deux organisations se distinguent par la disposition des clusters :

- le partitionnement dessine des clusters disjoints : les zones des clusters ne se chevauchent pas et chaque point n'appartient qu'à un seul groupe ;
- l'agrégation dessine des clusters imbriqués : un cluster intérieur est contenu dans un cluster plus large, et un point du cluster intérieur appartient aussi au cluster qui l'englobe.

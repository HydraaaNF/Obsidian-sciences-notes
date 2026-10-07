# Définition

Chaque point est étiqueté selon le nombre de points présents autour de lui :

- **Point core** : point qui a suffisamment de points autour de lui.
- **Point border** : point qui n'a pas suffisamment de points autour de lui, mais qui est proche d'un point core.
- **Point noise** : point qui n'est ni core ni border.

Le repérage de ces points repose sur les deux paramètres du [[DBSCAN]] : le rayon du voisinage et le nombre minimal de points qu'il doit contenir.

# Interprétation

Les clusters se forment à partir des points core, les points border y sont rattachés et les points noise sont éliminés. C'est le principe du [[Clustering par densité]] et de l'algorithme [[DBSCAN]].

# Exemple

Sur un nuage de points, chaque point examiné est muni d'un voisinage circulaire de rayon $\text{Eps} = 1$ et le seuil est fixé à $\text{MinPts} = 4$ points : le point core est entouré d'assez de points, le point border n'a pas assez de points autour de lui mais reste proche d'un point core, et le point noise n'est ni l'un ni l'autre.

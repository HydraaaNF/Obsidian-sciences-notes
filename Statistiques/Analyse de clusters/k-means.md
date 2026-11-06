# Définition

Le k-means est une méthode de [[Clustering|clustering]] qui partitionne des données en $k$ clusters, chacun représenté par son centre. C'est une formulation de problème, et non un algorithme.

Étant donné un espace et une distance euclidiens (voir [[Mesures de similarité et de distance]]), ainsi que $k = \text{nombre de clusters}$ (voir [[Choix du nombre de clusters]]), il s'agit de trouver les centres de clusters qui minimisent la somme des distances au carré de chaque point à son centre de cluster.

# Modèle

- **Données** : des exemples $\{x_1,\ldots,x_N\}$, avec $x_i \in \mathbb{R}^d$.
- **Centres** : $\{c_1,\ldots,c_K\}$, avec $c_i \in \mathbb{R}^d$.
- **Fonction d'affectation** : $f : [1,N] \to [1,K]$, où $f(i)$ est l'indice du cluster (ou du centre) affecté à l'exemple $i$.
- **Cluster** : $S_k = \{x_i : f(i) = k\}$.
- **Inertie** : $\sum_k \sum_{x \in S_k} \lVert x - c_k \rVert^2$.

# Interprétation

Sur un nuage de points en deux dimensions, chaque cluster est muni de son centre (croix) et chaque point est relié à son centre par un trait pointillé ; l'inertie est la somme des carrés des longueurs de ces traits.

# Propriétés

- Trouver une solution exacte est NP-difficile.
- La solution approchée est l'[[Algorithme des k-moyennes de Lloyd|algorithme de Lloyd]], ou l'algorithme des k-moyennes.
- Le choix de la distance est déterminant : la **moyenne** doit avoir un sens pour la distance choisie ; sinon on peut utiliser la médiane, voir [[k-médianes et k-médoïdes]].
- La convergence est garantie, généralement en 10 à 20 itérations ; la complexité est $O(iKNd)$, où $i$ est le nombre d'itérations et $d$ la dimension des $x_i$.
- L'initialisation est un point sensible : voir le choix aléatoire, les exécutions multiples, ou l'initialisation hiérarchique de [[k-means hiérarchique de Linde-Buzo-Gray]].

# Exemple

Un premier exemple : des données en deux dimensions réparties en trois groupes compacts de points (losanges, cercles et carrés), chacun muni de son centre (croix) ; état de l'exécution à l'itération 6.

# Remarque

Les avantages et inconvénients du k-means sont détaillés dans [[Avantages et inconvénients du k-means]] ; ses propriétés et son algorithme dans [[Propriétés du k-means]] et [[Algorithme des k-moyennes de Lloyd]].

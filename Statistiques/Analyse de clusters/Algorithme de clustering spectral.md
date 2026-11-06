# Algorithme

L'**algorithme de clustering spectral** réalise le [[Clustering spectral|clustering spectral]]. À partir d'une matrice de similarité, il construit le graphe de similarité, calcule son [[Laplacien du graphe]] $\mathbf{L}$, puis applique l'algorithme des [[k-means|k-moyennes]] aux lignes de la matrice des vecteurs propres.

**Entrée :** matrice de similarité $\mathbf{S} \in \mathbb{R}^{n \times n}$, nombre de clusters $k$.

L'algorithme procède en six étapes :

1. construire le graphe de similarité à partir de $\mathbf{S}$, de matrice d'adjacence $\mathbf{W}$ ;
2. calculer le Laplacien $\mathbf{L}$ ;
3. calculer les $k$ vecteurs propres $\mathbf{u}_1, \ldots, \mathbf{u}_k$ de $\mathbf{L}$ associés aux $k$ plus petites valeurs propres ;
4. définir $\mathbf{U} \in \mathbb{R}^{n \times k}$ ayant $\mathbf{u}_1, \ldots, \mathbf{u}_k$ pour colonnes ;
5. définir $\mathbf{y}_i \in \mathbb{R}^k$ comme la $i$-ème ligne de $\mathbf{U}$, pour $i \in [1, n]$ ;
6. exécuter l'algorithme des k-moyennes (ou un autre) sur le vecteur $\mathbf{y}_i$.

# Remarque

L'algorithme présente des liens forts avec les algorithmes de coupe de graphe (NCut, RatioCut, MinMaxCut) et avec la théorie des marches aléatoires (Markov clustering).

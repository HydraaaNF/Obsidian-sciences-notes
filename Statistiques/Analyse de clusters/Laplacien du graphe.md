# Définition

Le Laplacien non normalisé d'un graphe est la matrice $n \times n$ définie par

$$\mathbf{L} = \mathbf{D} - \mathbf{W}$$

où $\mathbf{D}$ est une matrice diagonale d'éléments $d_i = \sum_j w_{ij}$.

# Propriétés

Les propriétés importantes de $\mathbf{L}$ sont les suivantes :

- $\mathbf{L}$ possède $n$ valeurs propres réelles positives ou nulles ;
- la plus petite valeur propre est $0$ et correspond au vecteur propre unité $\mathbf{1}$ ;
- la multiplicité de la valeur propre $0$ est le nombre de composantes connexes.

# Interprétation

Les valeurs propres du Laplacien du graphe de similarité s'exploitent pour effectuer un clustering : c'est le principe du [[Clustering spectral]], que met en œuvre l'[[Algorithme de clustering spectral]].

# Remarque

Des versions normalisées du Laplacien sont souvent utilisées en pratique.

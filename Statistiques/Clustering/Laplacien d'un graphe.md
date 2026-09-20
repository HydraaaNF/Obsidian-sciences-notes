# Définition
Pour un graphe pondéré de matrice d'adjacence $W$ (poids $w_{ij}$ entre les nœuds $i$ et $j$), le **Laplacien non normalisé** est la matrice $n \times n$
$$L = D - W$$
où $D$ est la matrice diagonale de coefficients $d_i = \sum_j w_{ij}$.

# Propriétés
- $L$ a $n$ valeurs propres réelles, toutes positives ou nulles
- sa plus petite valeur propre est $0$, associée au vecteur propre $\mathbb{1}$ (le vecteur constant)
- la **multiplicité** de la valeur propre $0$ est égale au **nombre de composantes connexes** du graphe

# Interprétation
Ces propriétés permettent d'exploiter les valeurs propres du Laplacien pour effectuer un clustering — voir [[Classification spectrale]].

# Remarque
En pratique, on utilise plus souvent des versions **normalisées** du Laplacien.

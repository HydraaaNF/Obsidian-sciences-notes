# Définition

La **matrice de corrélation** de $p$ variables observées sur $n$ individus est la matrice $p \times p$ dont le coefficient $(i, j)$ est le [[Covariance et coefficient de corrélation linéaire|coefficient de corrélation linéaire]] entre les variables $i$ et $j$. Elle rassemble en un seul tableau toutes les corrélations linéaires deux à deux entre les variables d'un jeu de données.

# Propriétés

- La matrice de corrélation est **symétrique** : $r_{ij} = r_{ji}$.
- Sa **diagonale** vaut $1$ : $r_{ii} = 1$.
- Ses coefficients sont **compris entre $-1$ et $1$** : $r_{ij} \in [-1, 1]$.
- Elle se relie à la matrice de covariance par $r_{ij} = \dfrac{c_{ij}}{s_i s_j}$, où $c_{ij}$ est la [[Covariance empirique|covariance empirique]] de $X_i$ et $X_j$ et $s_i$, $s_j$ leurs [[Variance et écart-type|écarts-types empiriques]].
- Elle permet de lire d'un coup d'œil les liaisons entre toutes les paires de variables et sert de point de départ à l'[[Analyse en composantes principales]].

# Remarque

À ne pas confondre avec [[Matrice des nuages de points]].

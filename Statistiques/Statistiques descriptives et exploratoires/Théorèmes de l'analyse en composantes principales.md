# Théorème 1

Si $F_k$ est le sous-espace de dimension $k$ d'inertie maximale, le sous-espace de dimension $k+1$ d'inertie maximale est la somme directe de $F_k$ et du sous-espace de dimension 1 orthogonal à $F_k$ d'inertie maximale.

Les solutions sont donc **emboîtées** : le sous-espace d'inertie maximale de dimension $k+1$ s'obtient en adjoignant à $F_k$ une direction orthogonale d'inertie maximale.

# Théorème 2

Le sous-espace $F_k$ est le sous-espace engendré par les $k$ vecteurs propres de $V$ associés aux $k$ plus grandes valeurs propres de $V$.

# Interprétation

Ces deux théorèmes fondent l'[[Analyse en composantes principales|analyse en composantes principales]]. Le premier énonce l'emboîtement des solutions, qui se construisent dimension par dimension ; le second les détermine au moyen des vecteurs propres de $V$, ce qu'exploite l'[[Algorithme de l'analyse en composantes principales]].

Ces sous-espaces satisfont les critères d'une [[Critères d'une bonne projection linéaire|bonne projection linéaire]] : conserver au mieux les distances entre individus et maximiser l'inertie des données projetées.

#ml-1

# Définition

Un **tenseur** d'ordre $n$ est un tableau à $n$ dimensions. L'**ordre** est le nombre de dimensions du tableau.

- ordre 0 : $7.5$ ;
- ordre 1 : $[7.5,\ -9,\ 1/4]$ ;
- ordre 2 : $[[7.5,\ 10,\ 3/5],\ [-9,\ 0,\ -1.2],\ [1/4,\ 4.1,\ -1]]$ ;
- ordre 3 : $T = [[[\dots],\ [\dots],\ [\dots]],\ [\dots],\ \dots]$, dont un élément s'écrit $T[i][j][k]$.

Un tenseur d'ordre 3 se lit selon trois axes, notés axis 1, axis 2 et axis 3.

# Exemple

Ordre des objets usuels :

- taille, niveau de gris : ordre 0 ;
- liste de mots : ordre 1 ;
- pixel : ordre 1 ;
- matrice de niveaux de gris : ordre 2 ;
- matrice de pixels : ordre 3.

# Propriétés

Qui peut le moins peut le plus : un ordre supérieur peut toujours héberger un ordre inférieur.

Une matrice peut ainsi stocker des vecteurs en lignes, et un tenseur d'ordre 3 des matrices en tranches.

# Remarque

Un vecteur est un tenseur d'ordre 1 et une matrice un tenseur d'ordre 2 : les données et leurs [[Donnée et attributs|attributs]] se représentent donc par des tenseurs.

En Python, ces tableaux multidimensionnels se manipulent avec les [[Tableaux NumPy et pandas|tableaux NumPy]] ou les [[Tenseurs PyTorch|tenseurs PyTorch]].

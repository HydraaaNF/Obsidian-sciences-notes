#ml-1

# Définition

NumPy fournit les tableaux de valeurs sur lesquels reposent les calculs sur vecteurs et tenseurs (voir [[Tenseur]]). Un tel tableau se crée avec `numpy.array` et se décrit par quatre attributs :

- `data` : les valeurs ;
- `dtype` : le type de chaque valeur ;
- `ndim` : le nombre de dimensions (l'ordre) ;
- `shape` : la taille de chaque dimension.

pandas est une couche au-dessus de NumPy. Il rend plus simples les opérations usuelles de traitement des données : colonnes nommées, types mêlés, valeurs manquantes, groupement.

Ses deux structures sont la Series et le DataFrame. Une Series est une colonne de valeurs nommée et indexée ; un DataFrame réunit plusieurs Series en colonnes alignées sur un même index.

# Exemple

Création d'un tableau à deux dimensions et découpage en lignes et en colonnes :

```python
import numpy

data = numpy.array([[11, 22, 33],
                    [44, 55, 66],
                    [77, 88, 99]])

print(data[0])

x, y = data[:, :-1], data[:, -1]
print(x)
print(y)
```

`print(data[0])` affiche la première ligne :

```
[11 22 33]
```

`data[:, :-1]` garde toutes les lignes et toutes les colonnes sauf la dernière, `data[:, -1]` garde la dernière colonne :

```
[[11 22]
 [44 55]
 [77 88]]
```

```
[33 66 99]
```

Le découpage (slicing) est ainsi la manière dont un jeu de données se sépare en entrées `x` et en étiquettes `y`.

Réunion de deux Series en un DataFrame, les deux colonnes partageant le même index :

| index | apples | oranges |
| --- | --- | --- |
| 0 | 3 | 0 |
| 1 | 2 | 3 |
| 2 | 0 | 7 |
| 3 | 1 | 2 |

# Remarque

`shape` est l'attribut que l'on affiche le plus souvent : la plupart des bugs rencontrés en travaux pratiques sont des incompatibilités de forme entre tableaux.

Pour l'alignement de dimensions de formes différentes, voir [[Diffusion entre tenseurs]] ; pour les tableaux de PyTorch, voir [[Tenseurs PyTorch]].

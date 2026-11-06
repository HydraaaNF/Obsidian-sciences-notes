# Définition

La **matrice de proximité** rassemble les proximités entre clusters : chaque ligne et chaque colonne correspond à un cluster, et chaque case à la proximité du couple de clusters correspondant.

Dans le [[Clustering agglomératif et divisif|clustering agglomératif (ascendant)]], la matrice de proximité est mise à jour à chaque fusion : les deux lignes et les deux colonnes des clusters fusionnés sont remplacées par une seule ligne et une seule colonne, celles du cluster obtenu par leur union.

# Exemple

Partant de cinq clusters $C1$, $C2$, $C3$, $C4$ et $C5$, les deux clusters les plus proches, $C2$ et $C5$, sont fusionnés en un cluster unique noté $C2 \cup C5$. La matrice de proximité est mise à jour : les lignes et colonnes de $C2$ et de $C5$ disparaissent et sont remplacées par une ligne et une colonne $C2 \cup C5$.

La matrice mise à jour s'écrit :

|  | $C1$ | $C2 \cup C5$ | $C3$ | $C4$ |
|---|---|---|---|---|
| $C1$ |  | ? |  |  |
| $C2 \cup C5$ | ? | ? | ? | ? |
| $C3$ |  | ? |  |  |
| $C4$ |  | ? |  |  |

Les cellules marquées « ? » sont les proximités impliquant le nouveau cluster $C2 \cup C5$ ; leur valeur reste à déterminer. Le [[Types de liaison entre clusters|type de liaison]] précise la façon de mesurer la distance entre clusters.

# Remarque

Dans la matrice initiale, des hachures mettent en évidence les cellules concernées par la fusion : les lignes et colonnes de $C2$ et de $C5$, remplacées après la fusion par celles de $C2 \cup C5$. Ces hachures ne peuvent pas être reproduites dans un tableau markdown.

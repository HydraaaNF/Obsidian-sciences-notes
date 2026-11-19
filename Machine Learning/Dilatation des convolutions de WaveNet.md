#ml-2

# Définition

Dans [[Architecture WaveNet]], une **Residual Layer** est constituée de $N_U$ [[Unité résiduelle de WaveNet|Residual Units]] empilées, et le réseau complet est constitué de $N_L$ **Residual Layers**.

La dilatation de la [[Convolution dilatée]] est indexée par la couche $L$ et par l'unité $U$ à l'intérieur de cette couche :

$$d_{L,U} = 2^{U-1}$$

Chaque couche parcourt donc la progression $1, 2, 4, 8, \dots$, quel que soit son rang $L$.

# Propriétés

La dilatation double d'une unité à la suivante :

$$d_{L,U+1} = 2\,d_{L,U}$$

Une couche de trois unités utilise les dilatations $1, 2, 4$, dont la somme vaut $7$ :

$$1 + 2 + 4 = 7$$

Une couche de cinq unités utilise les dilatations $1, 2, 4, 8, 16$, dont la somme vaut $31$ :

$$1 + 2 + 4 + 8 + 16 = 31$$

Le champ récepteur de la pile se calcule à partir de ces sommes, selon la formule détaillée dans [[Champ récepteur d'une pile de convolutions]] :

$$\text{champ récepteur} = \left(\text{somme des dilatations} \times \text{nombre de couches} + 1\right)(k - 1) + 1$$

- Deux couches de trois unités, noyau $k = 2$ : $(7 \times 2 + 1) \times 1 + 1 = 16$.
- Trois couches de cinq unités, noyau $k = 2$ : $(31 \times 3 + 1) \times 1 + 1 = 95$.

# Interprétation

À l'intérieur d'une couche, le doublement de la dilatation d'une unité à la suivante fait croître le champ récepteur de façon exponentielle avec le nombre d'unités, sans augmenter le nombre de paramètres : à chaque unité, les $k$ poids du noyau sont réutilisés, seule la portée des connexions change.

À nombre d'unités fixé, le champ récepteur croît linéairement avec le nombre de couches, puisque chaque couche ajoute la même somme de dilatations.

La progression repart à $1$ au début de chaque couche, si bien que les couches successives relisent le signal à des échelles emboîtées : une unité de dilatation $1$ lit des échantillons voisins, une unité de dilatation $8$ relie des échantillons séparés par huit positions.

La causalité vient du padding causal à gauche de la [[Convolution causale]] : le noyau est décalé vers le passé, si bien qu'aucun échantillon futur n'entre dans le calcul. Le champ récepteur ne fait que mesurer l'étendue du passé consultée par chaque sortie.

# Exemple

Deux Residual Layers de trois Residual Units chacune, avec un noyau de taille $k = 2$.

- Première couche : dilatations $1, 2, 4$.
- Seconde couche : dilatations $1, 2, 4$.
- Somme des dilatations d'une couche : $1 + 2 + 4 = 7$.
- Champ récepteur : $(7 \times 2 + 1) \times 1 + 1 = 16$.

Les deux couches répètent la même progression, et c'est le nombre de couches qui multiplie la somme des dilatations.

# Remarque

L'écriture $2^{U} - 1$ donne la suite $1, 3, 7, \dots$ pour $U = 1, 2, 3$ ; elle ne double pas d'une unité à la suivante et contredit les champs récepteurs obtenus. Avec les dilatations $1, 3, 7$, la somme vaut $11$, d'où un champ de $(11 \times 2 + 1) \times 1 + 1 = 24$ au lieu de $16$ ; avec $1, 3, 7, 15, 31$, la somme vaut $57$, d'où un champ de $(57 \times 3 + 1) \times 1 + 1 = 173$ au lieu de $95$. La forme correcte est $d_{L,U} = 2^{U-1}$.

L'égalité $2^3 - 1 = 4$ est une erreur de calcul : $2^3 = 8$, donc $2^3 - 1 = 7$. Les valeurs $1, 2, 4$ sont celles de $2^{U-1}$ pour $U = 1, 2, 3$, et non celles de $2^{U} - 1$.

Pour $U = 1$, la dilatation vaut $1$ : la première unité de chaque couche se réduit à une convolution non dilatée.

La causalité d'une pile dilatée est parfois attribuée au champ récepteur ; elle vient en réalité du padding causal à gauche, qui seul écarte les échantillons futurs du calcul. Le champ récepteur mesure l'étendue du passé consultée ; il ne garantit pas la causalité.

Le même symbole $N$ sert souvent à la fois pour le nombre de couches et pour le nombre d'unités ; on note ici $N_L$ le nombre de Residual Layers et $N_U$ le nombre de Residual Units par couche.

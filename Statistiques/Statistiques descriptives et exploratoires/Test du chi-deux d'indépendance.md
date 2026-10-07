# Définition

Le **test du chi-deux d'indépendance** mesure l'écart à l'[[Indépendance de deux caractères|indépendance empirique]] entre deux caractères qualitatifs $X$ et $Y$ observés sur une [[Population statistique et caractère|population]], à partir des effectifs de leur [[Tableau de contingence]]. Il s'appuie sur la statistique

$$\chi^2 = \sum_i \sum_j \frac{\left(n_{ij} - \frac{n_{i.} \cdot n_{.j}}{n}\right)^2}{\frac{n_{i.} \cdot n_{.j}}{n}},$$

où $n_{ij}$ désigne l'effectif observé de la case $(i, j)$, $n_{i.}$ le total de la ligne $i$, $n_{.j}$ le total de la colonne $j$ et $n$ l'effectif total. Les deux caractères sont empiriquement indépendants lorsque tous les profils lignes et tous les profils colonnes du tableau sont identiques, c'est-à-dire lorsque $n_{ij} = \frac{n_{i.} \cdot n_{.j}}{n}$ pour tous $i$ et $j$ : chaque terme de la somme compare ainsi l'effectif observé $n_{ij}$ à l'effectif attendu sous cette indépendance, $n_{i.} \cdot n_{.j} / n$.

# Interprétation

La statistique $\chi^2$ est une mesure d'association entre les deux caractères : elle s'annule en cas d'indépendance empirique parfaite et devient d'autant plus grande que les effectifs observés s'écartent des effectifs attendus. Plus $\chi^2$ est grand, plus l'hypothèse d'indépendance entre $X$ et $Y$ est mise en doute.

# Exemple

Sur le [[Tableau de contingence|tableau de contingence]] latéralité × sexe (100 personnes), les effectifs théoriques sous indépendance sont $n_{ij} = \frac{n_{i.} n_{.j}}{n}$ :

| | Droitier (théorique) | Gaucher (théorique) |
|---|---|---|
| Homme | 45,24 | 6,76 |
| Femme | 41,76 | 6,24 |

$$\chi^2 = \frac{(43-45{,}24)^2}{45{,}24} + \frac{(9-6{,}76)^2}{6{,}76} + \frac{(44-41{,}76)^2}{41{,}76} + \frac{(4-6{,}24)^2}{6{,}24} \approx 1{,}78$$

Le calcul détaillé du $\chi^2$ ci-dessus rend l'exemple exploitable de bout en bout.

# Remarque

Le nom du test provient de sa statistique $\chi^2$ : la [[Loi du chi-deux|loi du chi-deux]] est la loi de référence à laquelle cette statistique est comparée pour conclure le test.

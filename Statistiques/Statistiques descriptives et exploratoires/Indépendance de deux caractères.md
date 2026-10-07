# Définition

Deux caractères qualitatifs $X$ et $Y$ observés sur une [[Population statistique et caractère|population]] sont **empiriquement indépendants** si tous les profils lignes et tous les profils colonnes de leur [[Tableau de contingence]] sont identiques : la répartition des individus selon l'un des caractères ne dépend alors pas de la modalité prise par l'autre.

Cette indépendance empirique s'écrit, pour tous $i$ et $j$,

$$n_{ij} = \frac{n_{i.} \cdot n_{.j}}{n},$$

où $n_{ij}$ désigne l'effectif de la case $(i, j)$, $n_{i.}$ le total de la ligne $i$, $n_{.j}$ le total de la colonne $j$ et $n$ l'effectif total.

# Exemple

Tableau de contingence croisant le sexe et la main dominante :

|  | Droitiers | Gauchers | Total |
|---|---|---|---|
| Hommes | 43 | 9 | 52 |
| Femmes | 44 | 4 | 48 |
| Total | 87 | 13 | 100 |

Les profils lignes ne sont pas identiques : la proportion de gauchers vaut $9/52$ chez les hommes contre $4/48$ chez les femmes, de sorte que les deux caractères ne sont pas empiriquement indépendants dans cet exemple.

# Remarque

L'écart à l'indépendance empirique se mesure par la statistique $\chi^2$ du [[Test du chi-deux d'indépendance|test du chi-deux d'indépendance]].

Pour le passage des effectifs d'un tableau de contingence aux fréquences, voir [[Fréquences conjointes, marginales et conditionnelles]].

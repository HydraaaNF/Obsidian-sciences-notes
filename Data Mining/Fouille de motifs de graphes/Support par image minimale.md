#dmv-graph_mining

# Définition

Soit $D$ un [[Collection de graphes et graphe unique|graphe unique]] et $P$ un motif de graphe. Le support par image minimale de $P$ dans $D$ est

$$\text{Support}(P) = \min_{v \in V^P} \left| \{\varepsilon(v) \mid \varepsilon \text{ est un plongement de } P \text{ dans } D\} \right|$$

Pour chaque sommet $v$ du motif, on considère l'ensemble des sommets de $D$ sur lesquels $v$ est envoyé par un plongement de $P$, et on retient le plus petit de ces ensembles : le support est le nombre minimal d'images distinctes d'un sommet du motif.

# Exemple

Le motif est une chaîne de quatre sommets : un sommet blanc, un sommet foncé, un sommet gris et un sommet blanc. Quatre plongements $A$, $B$, $C$, $D$ de ce motif sont relevés dans le graphe de données, ce qui donne l'image de chaque sommet du motif.

| Sommet du motif | A | B | C | D | Images distinctes |
| --- | --- | --- | --- | --- | --- |
| 1 (blanc) | 8 | 1 | 1 | 9 | 3 |
| 2 (foncé) | 5 | 3 | 3 | 7 | 3 |
| 3 (gris) | 2 | 6 | 6 | 4 | 3 |
| 4 (blanc) | 1 | 8 | 9 | 1 | 3 |

Chaque ligne ne prend que 3 valeurs distinctes, d'où un support de 3.

Sur le graphe de films et d'acteurs, les trois motifs élémentaires donnent :

| Motif | Occurrences de sommets | Support |
| --- | --- | --- |
| sommet film (ellipse) | 3 sommets de données | 3 |
| sommet acteur (rectangle) | 6 sommets de données | 6 |
| arête film → acteur | 2 sommets de données pour le film, 6 pour l'acteur | 2 |

Pour le motif arête, le sommet film ne peut être l'image que d'un film ayant au moins un acteur dans son casting, donc de 2 films seulement, alors que le sommet acteur peut être l'image des 6 acteurs. Le plus petit des deux ensembles d'images donne le support 2.

# Propriétés

- Le support par image minimale est [[Anti-monotonie du support dans une collection de graphes|anti-monotone]].
- Son calcul ne demande la résolution d'aucun problème NP-complet.

# Remarque

Le [[Support naïf par comptage d'occurrences|support naïf]] donnait 3, 6 et 7 pour ces trois motifs, et le [[Support par chevauchement]] donnait 2 pour le motif arête : sur cet exemple les deux mesures corrigées coïncident, mais seule l'image minimale évite de résoudre un problème NP-complet.

Le chevauchement demande en effet le calcul du MIS (ensemble indépendant de cardinal maximum), problème NP-complet, dont l'image minimale se passe ; en contrepartie, l'image minimale suppose les plongements déjà connus, leur énumération restant un problème d'[[Isomorphisme de sous-graphe|isomorphisme de sous-graphe]].

L'image minimale borne le nombre de occurrences utiles par le nombre d'images distinctes d'un sommet : un sommet du motif très contraint, qui ne peut se placer que sur peu de sommets de données, plafonne le support du motif entier.

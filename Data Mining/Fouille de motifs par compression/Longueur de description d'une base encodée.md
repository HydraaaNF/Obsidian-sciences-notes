#dmv-pattern_mining_with_information_theory

# Définition

Soit $D$ une base de transactions et $CT$ une [[Table de codes]]. La longueur de description d'une transaction $t$ de $D$ encodée avec $CT$ est la somme des longueurs des codes retenus dans son [[Couverture d'une transaction par une table de codes|cover]] :

$$L(t \mid CT) = \sum_{c \in cover(t, CT)} L(c \mid CT)$$

La longueur de description de la base $D$ encodée avec $CT$ est la somme de ces longueurs sur toutes les transactions :

$$L(D \mid CT) = \sum_{t \in D} L(t \mid CT)$$

# Interprétation

Une transaction se paie au nombre de codes que son cover retient, chacun facturé à sa propre longueur. Une transaction dont les items se retrouvent groupés dans une entrée de la table se décrit donc avec un seul code, alors qu'une transaction dont les items ne se regroupent dans aucune entrée se paie un code par item.

La longueur $L(c \mid CT)$ décroît avec l'usage de l'entrée $c$, selon la [[Probabilité et longueur optimale d'un code|longueur optimale d'un code]]. La base se décrit d'autant plus court que les itemsets de la table correspondent à des combinaisons fréquentes, puisque celles-ci reçoivent alors des codes courts et couvrent beaucoup de transactions.

La somme des usages des entrées de $CT$ est exactement le nombre total de codes émis pour encoder $D$ :

$$\sum_{c \in CT} usage(c) = \sum_{t \in D} \lvert cover(t, CT) \rvert$$

# Exemple

Avec la [[Table de codes standard]] d'une base de huit transactions, dont cinq $A\ B\ C$, une $A\ B$, une $A$ et une $B$, le cover de chaque transaction se réduit à ses propres items :

- la transaction $A\ B\ C$ coûte trois codes, ceux de $\{A\}$, $\{B\}$ et $\{C\}$,
- la transaction $A\ B$ coûte deux codes,
- la transaction $A$ coûte un code,
- la transaction $B$ coûte un code.

La longueur $L(D \mid ST)$ vaut donc $5 \times 3 + 2 + 1 + 1 = 19$ codes, et les usages de la table valent $7$, $7$ et $5$, soit également un total de $19$ : longueur totale et somme des usages coïncident, chaque transaction émettant exactement un code par entrée de son cover.

# Remarque

$L(D \mid CT)$ ne mesure que le second terme de la description : la table elle-même doit aussi être décrite, et c'est la somme des deux qui décide de la qualité du modèle, la [[Taille totale d'un modèle et des données encodées]].

La longueur dépend de la table par deux chemins à la fois : elle fixe les itemsets disponibles pour le cover, et elle fixe les usages, donc les longueurs de code. Remplacer une seule entrée de $CT$ modifie les usages de plusieurs autres entrées, et par suite les longueurs de tous les codes concernés : $L(D \mid CT)$ se recalcule entièrement à chaque modification de la table, ce qui pèse sur la [[Recherche de la table de codes optimale]].

Comme le cover, la longueur dépend de l'ordre des codes dans la table : deux tables portant les mêmes itemsets mais dans un ordre différent peuvent couvrir les transactions différemment, et donc leur attribuer des longueurs différentes.

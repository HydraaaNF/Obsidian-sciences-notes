#dmv-pattern_mining_with_information_theory
# Définition

La table de codes standard d'une base $D$, notée $ST$, est la [[Table de codes]] qui contient tous les itemsets singletons et seulement eux : une entrée $\{i\}$ pour chaque item $i$ présent dans $D$.

Son usage se lit directement sur les données : l'entrée $\{i\}$ a pour usage le nombre de transactions de $D$ qui contiennent $i$.

# Exemple

Base de huit transactions :

| Transaction |
| --- |
| A B C |
| A B C |
| A B C |
| A B C |
| A B C |
| A B |
| A |
| B |

La table de codes standard correspondante compte une entrée par item, avec les usages suivants :

| Itemset | Usage |
| --- | --- |
| {A} | 7 |
| {B} | 7 |
| {C} | 5 |

L'item $A$ apparaît dans les cinq transactions $A\ B\ C$, dans $A\ B$ et dans $A$, soit $5 + 1 + 1 = 7$ occurrences ; de même pour $B$ ; l'item $C$ n'apparaît que dans les cinq transactions $A\ B\ C$, soit $5$.

Le [[Couverture d'une transaction par une table de codes|cover]] de chaque transaction se réduit à ses propres items, puisque toutes les entrées sont des singletons : la transaction $A\ B\ C$ a pour cover $A$, $B$, $C$, la transaction $A\ B$ a pour cover $A$, $B$, la transaction $A$ a pour cover $A$ et la transaction $B$ a pour cover $B$.

L'encodage avec $ST$ juxtapose donc un code par item :

- $A\ B\ C$ s'encode avec trois codes (celui de $A$, celui de $B$, celui de $C$),
- $A\ B$ s'encode avec deux codes (celui de $A$, celui de $B$),
- $A$ s'encode avec un seul code,
- $B$ s'encode avec un seul code.

# Remarque

La table de codes standard est le cas particulier de [[Table de codes]] réduit aux itemsets singletons : elle ne contient aucun itemset de plusieurs items, donc aucune régularité à exploiter, et chaque transaction s'y encode item par item. Elle sert de table de départ aux heuristiques de recherche, en particulier à l'[[Algorithme KRIMP]], qui l'enrichit ensuite d'itemsets plus longs.

Comme $ST$ ne dépend que des données et pas du modèle construit, elle fournit une unité de mesure fixe pour décrire les itemsets d'une autre table de codes, ce qui permet de chiffrer la [[Longueur de description d'une table de codes]].

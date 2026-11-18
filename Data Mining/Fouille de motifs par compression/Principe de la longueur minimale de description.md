#dmv-pattern_mining_with_information_theory

# Définition

Le principe de la longueur minimale de description (MDL) énonce : « Le modèle qui décrit le mieux les données est celui qui les compresse le mieux. »

# Interprétation

Un modèle décrit les données parce qu'il en capture les régularités ; il les compresse donc, de façon abstraite. Le principe rend cette observation concrète : décrire et compresser sont un seul et même objectif, et le meilleur modèle est celui qui donne la description la plus courte des données.

# Exemple

La base est la séquence de onze symboles :

$$D = a\,b\,c\,c\,a\,b\,c\,d\,a\,b\,c$$

Le motif $abc$ y apparaît trois fois. En le remplaçant par un code court, la base se réécrit avec cinq symboles seulement, et le modèle $M$ associe un code à chaque motif :

| Motif | Code |
|---|---|
| $abc$ | violet |
| $c$ | vert |
| $d$ | orange |

La base réécrite vaut « violet, $c$, violet, $d$, violet », puis les données encodées avec $M$, notées $D \mid M$, sont la suite des cinq codes :

$$D \mid M = \text{violet},\ \text{vert},\ \text{violet},\ \text{orange},\ \text{violet}$$

Un motif qui apparaît trois fois reçoit un code court ; un motif qui apparaît une seule fois reçoit un code long.

# Remarque

La compression ne se réduit pas au remplacement des répétitions : le meilleur modèle résulte d'un arbitrage entre la longueur du modèle et celle des données encodées, traité dans [[Compromis entre longueur du modèle et longueur des données]]. Le modèle prend ici la forme d'une [[Table de codes]], et la [[Complexité de Kolmogorov]] fournit la borne que le principe approche en pratique.

#dmv-sequence_mining

# Définition

- Une **base de séquences** est un ensemble de séquences, chacune repérée par un identifiant de séquence (SID).
- Une **séquence** est une suite **ordonnée** d'éléments ou d'événements, et c'est cet ordre qui porte la chronologie.
- Un élément d'une séquence peut regrouper plusieurs items simultanés ; c'est alors un itemset, et une séquence s'écrit $\langle a(abc)(ac)d(cf)\rangle$, chaque groupe entre parenthèses formant un élément et les éléments se succédant de gauche à droite.
- L'**horodatage** des éléments est soit explicite, une date étant attachée à chaque élément, soit implicite, la position de l'élément dans la séquence en tenant lieu.

# Modèle

Le passage des transactions d'un client à une base de séquences se fait en conservant la chronologie des achats :

- chaque transaction devient un élément de la séquence, et les items qu'elle contient sont simultanés ;
- l'ordre chronologique des transactions fixe l'ordre des éléments ;
- la date de la transaction fournit l'horodatage de l'élément.

Ce qui est recherché dans une telle base est une **répétition** d'éléments, en tenant compte de la chronologie entre les transactions : c'est l'objet de la [[Lecture informelle d'un motif séquentiel|lecture informelle d'un motif séquentiel]], formalisée par la notion de [[Motif séquentiel|motif séquentiel]].

# Exemple

Historique d'achats d'un client, cinq transactions datées de 2005 :

- 1er janvier 2005 : Caviar, Wine
- 1er février 2005 : Beer, Vegetable
- 1er avril 2005 : Chocolate
- 1er juin 2005 : Beer, Chocolate, Bread, Vegetable
- 31 décembre 2005 : Chocolate, Champagne

Une répétition cherchée sur cet historique est $\langle (\text{Beer Vegetable})(\text{Chocolate}) \rangle$ : les deux items Beer et Vegetable sont achetés ensemble le 1er février, puis Chocolate est acheté après eux, le 1er avril suivant. Le motif ne retient donc pas seulement la cooccurrence des items, mais leur succession dans le temps.

Mise en regard d'une base de transactions et d'une base de séquences sur les mêmes identifiants 10, 20, 30, 40 :

| TID | itemsets |
| :-: | :-: |
| 10 | $a\ b\ d$ |
| 20 | $a\ c\ d$ |
| 30 | $a\ d\ e\ f$ |
| 40 | $e\ f$ |

| SID | sequences |
| :-: | :-: |
| 10 | $\langle a(abc)(ac)d(cf)\rangle$ |
| 20 | $\langle (ad)c(bc)(ae)\rangle$ |
| 30 | $\langle (ef)(ab)(df)cb\rangle$ |
| 40 | $\langle eg(af)cbc\rangle$ |

Dans ce tableau, l'horodatage est implicite : seule la position des éléments dans la séquence marque le temps.

Lorsque les transactions sont converties en séquences d'itemsets datées, la date de chaque transaction devient l'horodatage de l'élément. Sur quatre séquences $S_1$ à $S_4$ observées sur quatre jours :

| SeqId | Monday ($d_1$) | Tuesday ($d_2$) | Wednesday ($d_3$) | Thursday ($d_4$) |
| :-: | :-: | :-: | :-: | :-: |
| $S_1$ | $abc$ | $bde$ | $abf$ | $ad$ |
| $S_2$ | $abc$ | $abc$ | - | $bcf$ |
| $S_3$ | $bce$ | - | $adf$ | $abc$ |
| $S_4$ | $acf$ | $bd$ | $abf$ | $e$ |

Chaque cellule est un élément de la séquence : $S_1 = \langle (abc)(bde)(abf)(ad) \rangle$. Le tiret marque un jour sans achat, donc un élément absent de la séquence.

# Remarque

Selon la manière dont le temps est porté, deux lectures d'une même base coexistent : un horodatage explicite, une date par élément, comme dans l'historique d'achats daté ; un horodatage implicite, la position de l'élément suffisant à ordonner la séquence, comme dans les séquences $\langle a(abc)(ac)d(cf)\rangle$. La [[Support d'un motif séquentiel|fréquence d'un motif]] se compte de la même façon dans les deux cas, un motif étant contenu dans une séquence dès que ses éléments y apparaissent dans le bon ordre.

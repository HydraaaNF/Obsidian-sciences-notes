#dmv-frequent_itemsets_mining

# Définition

Une [[Items, itemsets et base de transactions|base de transactions]] se range en mémoire de deux façons.

Le **format horizontal** range la base en une ligne par transaction : chaque ligne est un identifiant de transaction (tid) accompagné des items qu'elle contient. C'est le format de travail de l'[[Algorithme Apriori]] : pour compter le support d'un itemset, il faut tester son inclusion dans chacune des transactions, ce qui suppose d'énumérer les sous-ensembles de la transaction ou d'indexer les candidats dans un [[Arbre de hachage et comptage du support|arbre de hachage]].

Le **format vertical** range la base en une entrée par item : à chaque item $a$ est associée sa **tidlist**, la liste des tids des transactions qui contiennent $a$,

$$a \mapsto \mathrm{tidlist}(a)$$

La tidlist d'un itemset est l'intersection des tidlists de ses items, si bien que le support se lit comme le cardinal d'un ensemble de tids et non comme le résultat d'un test d'inclusion répété sur les transactions :

$$\mathrm{tidlist}(I \cup J) = \mathrm{tidlist}(I) \cap \mathrm{tidlist}(J)$$

Le format vertical est le point de départ de l'[[Algorithme Eclat]], qui convertit la base dans cette représentation avant de décomposer les itemsets fréquents de taille deux en classes d'équivalence.

# Exemple

Base de six transactions sur les cinq items A, B, C, D, E, en format horizontal :

| Transaction | A | B | C | D | E |
| :-: | :-: | :-: | :-: | :-: | :-: |
| 1 | X | X | X | X | X |
| 2 | X | X | X | | X |
| 3 | | | X | | |
| 4 | | X | X | | |
| 5 | X | X | X | X | |
| 6 | X | X | X | | |

La même base en format vertical, une entrée par item :

| Item | Tidlist |
| :-: | :-: |
| A | 1, 2, 5, 6 |
| B | 1, 2, 4, 5, 6 |
| C | 1, 2, 3, 4, 5, 6 |
| D | 1, 5 |
| E | 1, 2 |

La conversion se lit en colonnes : l'item C figure dans les six transactions, l'item D seulement dans les transactions 1 et 5, l'item E seulement dans les transactions 1 et 2. Chaque tidlist a pour cardinal le support de l'item correspondant, soit $4$ pour A, $5$ pour B, $6$ pour C, $2$ pour D et $2$ pour E.

# Remarque

Le format vertical supprime le coût du comptage par test d'inclusion : plus besoin de tester les sous-ensembles de chaque transaction ni de construire un arbre de hachage des candidats, le support d'un itemset s'obtient par une intersection de tidlists, voir [[Support par intersection de tidlists]].

Sa limite est la place mémoire : sur une grosse base, les tidlists des nombreux candidats créés deviennent volumineuses et ne tiennent plus en mémoire. La parade consiste à partitionner le treillis des itemsets en [[Classes d'équivalence des itemsets|classes d'équivalence]] et à ne traiter qu'une classe à la fois ; Eclat retient comme relation d'équivalence le partage d'un même préfixe, ce qui ramène la fouille à un parcours en profondeur, comme le fait l'[[Algorithme Eclat]].

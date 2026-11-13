#dmv-frequent_itemsets_mining

# Interprétation

Le seuil de support minimum $minsup$ ne fixe pas seulement ce qui compte comme motif récurrent : il gouverne aussi le coût de l'extraction. Trois difficultés apparaissent à mesure que ce seuil baisse :

- le temps de calcul devient important ;
- pour les faibles valeurs de support, le nombre d'itemsets fréquents devient énorme ;
- le résultat contient une masse d'information redondante.

La redondance vient de l'hérédité de la fréquence : tout sous-ensemble d'un [[Itemset fréquent|itemset fréquent]] est fréquent, et il porte souvent exactement le même [[Support d'un itemset|support]] et le même tidlist que lui. Énumérer tous les itemsets fréquents revient alors à répéter plusieurs fois la même information.

# Exemple

Base de trois transactions :

| Tid | Transaction |
| :--- | :--- |
| 1 | A B C D |
| 2 | A B C |
| 3 | A B C E |

Avec $minsup = 2$, les itemsets fréquents sont :

| Itemset | Support | Tidlist |
| :--- | :---: | :---: |
| A B C | 3 | {1,2,3} |
| A B | 3 | {1,2,3} |
| A C | 3 | {1,2,3} |
| B C | 3 | {1,2,3} |
| A | 3 | {1,2,3} |
| B | 3 | {1,2,3} |
| C | 3 | {1,2,3} |

Les quatre itemsets $\{A, B, C\}$, $\{A, B\}$, $\{A, C\}$ et $\{B, C\}$ ont le même support $3$ et le même tidlist $\{1, 2, 3\}$, et les singletons $A$, $B$ et $C$ portent encore cette même information. Un seul itemset, $\{A, B, C\}$, la résume : les six autres sont redondants. Les items $D$ et $E$, présents dans une seule transaction chacun, ne sont pas fréquents.

# Remarque

Deux représentations condensées suppriment cette redondance sans énumérer tous les itemsets fréquents : les [[Itemsets fréquents fermés]], maximums des classes d'équivalence de même tidlist, et les [[Itemsets fréquents maximaux]], itemsets sans sur-ensemble fréquent. La seconde est la plus compacte, mais elle perd l'information de support des sous-ensembles ; la première la conserve. Le nombre d'itemsets produits par chaque représentation est comparé dans [[Nombre d'itemsets par type]].

Le calcul peut lui-même éviter l'énumération complète. La voie directe énumère tous les itemsets fréquents et ne retient que les fermés, ce qui reste inefficace sauf si l'ensemble des itemsets fréquents est très petit. La voie par fermeture ne calcule que les itemsets fermés, au moyen d'opérations de fermeture, et peut être très efficace.

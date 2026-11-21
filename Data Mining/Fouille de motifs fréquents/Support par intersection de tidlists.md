#dmv-frequent_itemsets_mining

# Définition

Dans le [[Format vertical des transactions|format vertical]], chaque item est accompagné de la liste des identifiants des transactions qui le contiennent, sa **tidlist**. Pour un itemset $X$, la tidlist est l'ensemble des transactions qui contiennent $X$ :

$$\mathrm{tidlist}(X) = \{j \mid X \subseteq t_j\}$$

Le [[Support d'un itemset|support]] de $X$ en est le cardinal, si bien que compter le support revient à compter des transactions communes.

# Propriétés

Pour tous itemsets $I$ et $J$, la tidlist de leur union est l'intersection de leurs tidlists :

$$\mathrm{tidlist}(I \cup J) = \mathrm{tidlist}(I) \cap \mathrm{tidlist}(J)$$

Le support de l'union est donc le nombre d'éléments de cette intersection :

$$\mathrm{support}(I \cup J) = |\mathrm{tidlist}(I) \cap \mathrm{tidlist}(J)|$$

Le comptage repose alors sur les seules intersections :

- aucun test d'inclusion $I \cup J \subseteq t$ n'est nécessaire, chaque transaction n'étant jamais reparcourue ;
- aucun [[Arbre de hachage et comptage du support|arbre de hachage]] n'est construit ni parcouru, la recherche des candidats contenus dans une transaction devenant inutile ;
- l'intersection de deux tidlists triées s'obtient en un parcours linéaire de chacune d'elles.

# Interprétation

La tidlist d'un item est la base conditionnelle de cet item : elle contient exactement les transactions où il apparaît. Intersecter la tidlist d'un item avec celle de chacun des autres items donne les supports de tous les itemsets portant ce préfixe, d'un seul passage sur les listes.

Le calcul descend ensuite en profondeur dans le treillis des itemsets : chaque intersection produit une tidlist plus courte, qui sert de point de départ au niveau suivant. Une tidlist vide interrompt la branche, aucun sur-ensemble ne pouvant être plus fréquent que son sous-ensemble.

# Exemple

Soit la base de dix transactions suivante :

| Transaction | Items |
|---|---|
| 1 | a, d, e |
| 2 | b, c, d |
| 3 | a, c, e |
| 4 | a, c, d, e |
| 5 | a, e |
| 6 | a, c, d |
| 7 | b, c |
| 8 | a, c, d, e |
| 9 | b, c, e |
| 10 | a, d, e |

Les tidlists des items sont :

- $\mathrm{tidlist}(a) = \{1, 3, 4, 5, 6, 8, 10\}$ ;
- $\mathrm{tidlist}(c) = \{2, 3, 4, 6, 7, 8, 9\}$ ;
- $\mathrm{tidlist}(d) = \{1, 2, 4, 6, 8, 10\}$ ;
- $\mathrm{tidlist}(e) = \{1, 3, 4, 5, 8, 9, 10\}$.

L'intersection avec la tidlist de $a$ donne les itemsets de préfixe $a$ :

- $\mathrm{tidlist}(\{a, c\}) = \{3, 4, 6, 8\}$ ;
- $\mathrm{tidlist}(\{a, d\}) = \{1, 4, 6, 8, 10\}$ ;
- $\mathrm{tidlist}(\{a, e\}) = \{1, 3, 4, 5, 8, 10\}$.

En poursuivant sur la branche issue de $\{a, c\}$ :

- $\mathrm{tidlist}(\{a, c, d\}) = \{4, 6, 8\}$ ;
- $\mathrm{tidlist}(\{a, c, e\}) = \{3, 4, 8\}$ ;
- $\mathrm{tidlist}(\{a, c, d, e\}) = \{4, 8\}$.

L'itemset $\{a, c, d\}$ a donc pour support $3$, obtenu sans examiner aucune transaction une seconde fois.

# Remarque

Le coût mémoire croît avec la base : sur une base volumineuse, les tidlists des nombreux candidats deviennent elles aussi volumineuses et ne tiennent plus en mémoire. La parade consiste à ne traiter qu'une partie du treillis à la fois, en le partitionnant en [[Classes d'équivalence des itemsets|classes d'équivalence]] dont les itemsets partagent un préfixe commun, ce que fait l'[[Algorithme Eclat]].


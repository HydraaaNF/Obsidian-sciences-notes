#dmv-frequent_itemsets_mining

# Algorithme

Eclat extrait les [[Itemset fréquent|itemsets fréquents]] d'une [[Items, itemsets et base de transactions|base de transactions]] $T$ pour un seuil de [[Support d'un itemset|support]] $minsup$. Il part des deux premiers niveaux calculés comme dans l'[[Algorithme Apriori|Apriori]], convertit la base au [[Format vertical des transactions|format vertical]], puis traite séparément les [[Classes d'équivalence des itemsets|classes d'équivalence]] du [[Treillis des itemsets|treillis]].

```text
Input: T, minsup

compute L_1 and L_2   // like apriori
Transform T in vertical representation
CE_2 = Decompose L_2 in equivalence classes
forall E_2 ∈ CE_2 do
    compute_frequent(E_2)
end forall

return ∪_k F_k ;
```

L'appel `compute_frequent` reçoit une classe d'équivalence $E_k$ d'itemsets fréquents de taille $k$ ; il la décompose à son tour en classes d'équivalence et se rappelle sur chacune d'elles, ce qui prolonge la fouille vers les itemsets plus longs : voir [[Algorithme de fouille d'une classe d'équivalence]].

# Interprétation

Les trois ingrédients de l'algorithme se lisent dans l'ordre de ses instructions.

**Le calcul des deux premiers niveaux.** $L_1$ et $L_2$ s'obtiennent comme avec Apriori : les singletons fréquents par un parcours de la base, puis les paires fréquentes en testant les paires d'items de $L_1$. Ces deux niveaux ne demandent aucune structure particulière, et c'est seulement à partir de la taille trois que la stratégie propre à Eclat entre en jeu.

**Le passage au format vertical.** La base est réorganisée en une entrée par item, chaque item étant muni de la tidlist des transactions qui le contiennent. Le support d'un itemset n'est plus obtenu en testant son inclusion dans chaque transaction, mais par une intersection de tidlists :

$$\mathrm{support}(I \cup J) = |\mathrm{tidlist}(I) \cap \mathrm{tidlist}(J)|$$

Le comptage ne demande plus de test d'inclusion sur chaque transaction, ni de génération d'[[Arbre de hachage et comptage du support|arbre de hachage]] pour retrouver les candidats qu'elle contient ; le détail du mécanisme est traité dans [[Support par intersection de tidlists]].

**La décomposition en classes d'équivalence.** Les itemsets de $L_2$ sont regroupés en classes partageant un même préfixe : la classe d'un item $a$ réunit les paires $\{a, x\}$ qui contiennent $a$. Le résultat est $CE_2$, partition de $L_2$. Chaque classe est ensuite confiée à `compute_frequent`, qui y cherche les extensions fréquentes en intersectant les tidlists des itemsets de la classe.

La fouille suit alors un parcours en profondeur : dans une classe de préfixe $P$, intersecter la tidlist de $P$ avec celles des autres items de la classe donne les supports de tous les itemsets portant ce préfixe. Une intersection dont le cardinal tombe sous $minsup$ écarte l'itemset et interrompt la branche, aucun sur-ensemble ne pouvant être plus fréquent ; les itemsets retenus descendent au niveau suivant avec une tidlist plus courte. Le déroulement complet de cette descente est décrit dans [[Recherche en profondeur d'Eclat]].

Le résultat est l'union des niveaux produits :

$$\bigcup_k F_k$$

# Remarque

Eclat conserve d'Apriori les deux premiers niveaux et le principe d'élagage fondé sur la [[Propriété d'anti-monotonie du support|propriété d'anti-monotonie du support]] : il ne cherche des itemsets de taille $k+1$ qu'à partir d'itemsets fréquents de taille $k$. Ce qui change est la façon de compter : plus de génération de candidats par [[Génération des candidats par apriori-gen|apriori-gen]], plus de comptage niveau par niveau sur les transactions, mais des intersections de tidlists menées branche par branche.

Le parcours en profondeur est ce qui rend la décomposition en classes utile : les tidlists d'une branche se déduisent l'une de l'autre par intersection, et une branche morte est abandonnée sitôt connue. C'est là toute la différence avec le parcours niveau par niveau d'Apriori, qui doit terminer un niveau entier avant de pouvoir filtrer ; les variantes d'élagage que la descente autorise sont exposées dans [[Recherche en profondeur d'Eclat]]. Le comportement des deux stratégies sur des bases réelles est comparé dans les [[Temps d'exécution comparés des algorithmes]].

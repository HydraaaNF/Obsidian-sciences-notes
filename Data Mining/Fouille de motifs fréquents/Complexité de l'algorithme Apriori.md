#dmv-frequent_itemsets_mining

# Propriétés

Le coût de l'[[Algorithme Apriori|algorithme Apriori]] s'analyse niveau par niveau. On note $C_k$ l'ensemble des candidats de taille $k$, $n$ le nombre d'items distincts et $m = |T|$ la taille de la [[Items, itemsets et base de transactions|base de transactions]], c'est-à-dire son nombre de transactions.

À l'étape $k$, la [[Génération des candidats par apriori-gen|génération des candidats]] est dominée par l'élagage, qui teste les $k$ sous-ensembles de taille $k-1$ de chaque candidat, de coût :

$$O(k\,|C_k|)$$

Le comptage du support sur toute la base a pour coût :

$$O(m\,|C_k|)$$

Une itération de l'algorithme, qui enchaîne ces deux traitements, coûte donc :

$$O(m\,|C_k|)$$

La complexité totale est la somme de ces coûts sur les niveaux effectivement parcourus :

$$O\!\left(m \sum_k |C_k|\right)$$

Dans le pire des cas, les candidats engendrés sont tous les itemsets possibles, si bien que $\sum_{k=1}^{n} |C_k| = 2^n - 1$ et que le coût devient :

$$O(m \cdot 2^n)$$

Deux lectures se dégagent de cette expression :

- la complexité est **linéaire en la taille de la base** : à itemsets candidats fixés, doubler le nombre de transactions double le travail de comptage ;
- elle est **exponentielle en le nombre d'items** : dans le pire cas, chaque item supplémentaire double le nombre d'itemsets à examiner.

# Interprétation

À chaque niveau, c'est le comptage du support qui fixe l'ordre de grandeur : l'élagage coûte $O(k\,|C_k|)$, le parcours de la base $O(m\,|C_k|)$, et $m$ dépasse en pratique largement $k$. Le travail utile de l'itération est donc proportionnel au produit du nombre de transactions et du nombre de candidats du niveau.

La croissance exponentielle porte sur le nombre d'items, pas sur la taille de la base : c'est la taille de l'ensemble des itemsets possibles, $2^n$, qui rend l'énumération exhaustive inapplicable dès que le nombre d'items devient grand. Le nombre de candidats effectivement engendrés reste très inférieur à ce pire cas, parce que l'élagage par la [[Propriété d'anti-monotonie du support|propriété d'anti-monotonie du support]] écarte les branches dont un sous-ensemble est déjà non fréquent.

Un troisième facteur intervient sur le coût du comptage : la largeur des transactions, c'est-à-dire la densité de la base. Plus les transactions contiennent d'items, plus chacune contient de candidats de $C_k$, et plus le nombre de parcours de l'[[Arbre de hachage et comptage du support|arbre de hachage]] augmente à nombre de transactions fixé.

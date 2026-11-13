#dmv-frequent_itemsets_mining

# Algorithme

`compute_frequent` est la procédure récursive de l'[[Algorithme Eclat]] : elle reçoit une classe d'équivalence $E_{k-1}$ d'itemsets fréquents de taille $k-1$ et y cherche les itemsets fréquents plus longs, une classe à la fois, au lieu de traiter le [[Treillis des itemsets|treillis]] entier.

Sur une classe $E_{k-1}$, la procédure procède en trois temps.

- Elle forme les paires d'itemsets $\{I_1, I_2\}$ de la classe et prend leur union $I_1 \cup I_2$ pour candidat ; dans le [[Format vertical des transactions|format vertical]], le support de ce candidat se lit directement sur les tidlists, par la [[Support par intersection de tidlists|propriété d'intersection des tidlists]].
- Elle retient les unions dont le support atteint le seuil, qui forment le niveau $L_k$.
- Elle décompose $L_k$ en classes d'équivalence $CE_k$, puis rappelle `compute_frequent` sur chaque classe.

Le support d'un candidat est le cardinal de l'intersection des tidlists de ses deux composantes :

$$\mathrm{support}(I_1 \cup I_2) = |\mathrm{tidlist}(I_1) \cap \mathrm{tidlist}(I_2)|$$

Le candidat est retenu dès que ce cardinal atteint le seuil :

$$|\mathrm{tidlist}(I_1) \cap \mathrm{tidlist}(I_2)| \ge minsup$$

La récursion s'arrête d'elle-même : l'intersection de tidlists ne produit plus aucune union admissible, ou la classe ne contient plus qu'un seul itemset, donc plus aucune paire à tester.

Le pseudocode se lit en deux blocs. La procédure principale calcule les deux premiers niveaux comme dans l'[[Algorithme Apriori|Apriori]], passe au [[Format vertical des transactions|format vertical]], puis lance la récursion :

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

Corps de `compute_frequent` : la boucle sur les paires de la classe se referme sur un `end forall`, puis le niveau produit $L_k$ est décomposé et chaque classe est traitée à son tour.

```text
    end forall

CE_k = Decompose L_k in equivalence classes
forall E_k ∈ CE_k do
    compute_frequent(E_k)
end forall
```

# Interprétation

La récursion inverse la logique d'Apriori. Apriori termine un niveau entier avant de passer au suivant et conserve tout l'arbre de recherche en mémoire ; `compute_frequent` descend au contraire dans une seule branche jusqu'à épuisement, puis revient traiter la classe suivante. Chaque appel travaille sur une fraction du treillis, ce qui borne la mémoire occupée par les tidlists au lieu de la faire croître avec le nombre de candidats du niveau.

Les tidlists forment la matière première de la descente. Celles de la classe $E_{k-1}$ sont connues quand la procédure est appelée : ce sont les intersections calculées au niveau précédent. Le test de support n'exige donc aucun parcours de la base, et une intersection vide ou trop courte élimine l'itemset sans autre calcul.

Le découpage en classes est ce qui rend la récursion possible. Les itemsets d'une même classe partagent un préfixe, si bien que leur union prolonge ce préfixe sans changer de branche du treillis ; les unions retenues au niveau $k$ sont à leur tour regroupées par préfixe, ce qui fournit les classes $CE_k$ que la procédure se rappelle sur chacune. La relation d'équivalence employée est donc celle du préfixe commun ; le mécanisme de ce découpage est décrit dans [[Classes d'équivalence des itemsets]].

# Remarque

Les classes traitées par `compute_frequent` sont les seules zones du treillis explorées : une classe dont le préfixe n'a produit aucun itemset fréquent n'est jamais formée, puisque $L_k$ ne contient que les unions admissibles. L'élagage de l'[[Propriété d'anti-monotonie du support|anti-monotonie du support]] est ainsi obtenu sans test explicite de sous-ensembles, le filtre du seuil s'appliquant à chaque intersection.

Le résultat de la procédure principale est l'union des niveaux produits :

$$\bigcup_k F_k$$

Chaque itemset fréquent y figure une seule fois, un itemset de taille $k$ n'appartenant qu'à une classe de $CE_k$.

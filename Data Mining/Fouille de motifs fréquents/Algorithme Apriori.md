#dmv-frequent_itemsets_mining

# Algorithme

Apriori extrait les [[Itemset fréquent|itemsets fréquents]] d'une [[Items, itemsets et base de transactions|base de transactions]] $T$ pour un seuil de [[Support d'un itemset|support]] $minsup$. Il procède par **recherche niveau par niveau** (levelwise) : il découvre d'abord les itemsets fréquents de taille 1, puis ceux de taille 2, et ainsi de suite.

```text
Input: T, minsup

F_1 = {Frequent 1-itemsets} ;
for (k=2 ; F_{k-1} ≠ ∅ ; k++) do begin
    C_k = apriori-gen(F_{k-1}) ; // candidates generation
    foreach transaction t ∈ T do begin
        C_t = subset(C_k, t) ; // Support counting
        foreach candidate c ∈ C_t do
            c.count++ ;
    end
    F_k = { c ∈ C_k | c.count ≥ minsup } ;
end
return ∪_k F_k ;
```

# Interprétation

Le niveau 1 s'obtient par un simple parcours de la base : chaque item dont le support atteint $minsup$ forme un itemset fréquent de taille 1, et $F_1$ est l'ensemble de ces singletons. Chaque tour de boucle construit ensuite le niveau $k$ à partir du niveau $k-1$ seulement.

Une itération enchaîne deux traitements :

- la **génération des candidats**, qui produit $C_k$ à partir de $F_{k-1}$ par la procédure [[Génération des candidats par apriori-gen|apriori-gen]] ;
- le **comptage du support**, qui parcourt chaque transaction $t$ de la base, extrait de $C_k$ les candidats contenus dans $t$ par l'appel `subset(C_k, t)`, et incrémente leur compteur. La recherche des candidats inclus dans une transaction s'appuie sur l'[[Arbre de hachage et comptage du support|arbre de hachage]] qui stocke $C_k$.

Le niveau se clôt par le filtrage qui ne retient que les candidats dont le compteur atteint le seuil :

$$F_k = \{c \in C_k \mid c.\mathit{count} \ge minsup\}$$

La boucle s'arrête dès que $F_{k-1}$ est vide : aucun itemset de taille $k-1$ n'étant fréquent, il n'existe plus de candidat de taille $k$ à examiner. Le résultat est l'union des niveaux produits :

$$\bigcup_k F_k$$

Chaque itemset fréquent apparaît donc une fois et une seule dans cette union, au niveau correspondant à sa taille, et aucun itemset de taille supérieure à celle du plus grand itemset fréquent n'est jamais construit. Cette union des niveaux, notée $F_{all}$, est l'entrée de la [[Génération des règles d'association|génération des règles d'association]].

# Remarque

L'algorithme exploite la [[Propriété d'anti-monotonie du support|propriété d'anti-monotonie du support]] : si un itemset n'est pas fréquent, aucun de ses sur-ensembles ne l'est. C'est elle qui autorise à ne générer les candidats de taille $k$ qu'à partir des itemsets fréquents de taille $k-1$, donc à ne jamais explorer les régions du [[Treillis des itemsets|treillis]] situées au-dessus d'un itemset écarté.

Deux précautions gouvernent l'usage de l'algorithme sur de grandes bases :

- le nombre de candidats peut devenir très grand à mesure que $k$ croît, ce qui rend le comptage du support coûteux ; l'ordre de grandeur du travail est analysé dans la [[Complexité de l'algorithme Apriori|complexité de l'algorithme Apriori]], et son effet sur les temps d'exécution mesurés se lit dans les [[Temps d'exécution comparés des algorithmes]] ;
- le parcours du niveau entier avant tout filtrage impose de stocker $C_k$ en mémoire, ce qui distingue cette stratégie du parcours en profondeur d'[[Algorithme Eclat|Eclat]], qui élague en cours de descente.

L'approche par force brute, qui énumère tous les itemsets possibles avant de compter leurs supports, est l'alternative naïve que cette organisation évite ; voir [[Limites de l'approche brute force]].

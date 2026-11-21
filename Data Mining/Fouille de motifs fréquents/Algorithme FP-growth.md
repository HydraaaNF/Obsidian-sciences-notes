#dmv-frequent_itemsets_mining

# Algorithme

FP-growth extrait les [[Itemset fréquent|itemsets fréquents]] en développant récursivement des motifs par leur préfixe, sans jamais générer de candidats. Il prend en entrée un [[Arbre FP]] et un préfixe d'items déjà validés.

```text
FP-growth(FP, prefix)

foreach frequent item x in increasing order of frequency do
    prefix = prefix ∪ x
    D_x = ∅
    count_x = 0
    foreach node-link nl_x of x do
        D_x = D_x ∪ {transaction of path reaching x, with count for each item = nl_x.count, without x}
        count_x += nl_x.count
    end
    if count_x ≥ minsup then
        output (prefix ∪ x)
        FP_x = FP-tree constructed from D_x
        FP-growth(FP_x, prefix)
    end if
end
```

# Interprétation

Chaque appel traite un arbre et un préfixe, et énumère les items fréquents de l'arbre par fréquence croissante, donc en commençant par les items les moins fréquents.

Pour un item $x$ donné, l'algorithme construit sa **base conditionnelle** $D_x$ :

- il suit la chaîne de liens de nœuds de $x$, c'est-à-dire la liste des nœuds portant le nom $x$ dans les différentes branches de l'arbre ;
- pour chaque nœud atteint, il extrait le chemin qui mène de la racine à ce nœud, affecte à chaque item du chemin le compteur du nœud, et retire l'item $x$ lui-même ;
- il réunit ces chemins pondérés dans $D_x$, qui ne contient donc que les transactions où figure $x$, réduites à leur préfixe.

En parallèle, les compteurs rencontrés le long de la chaîne sont cumulés dans $count_x$. Cette somme est le nombre de transactions contenant le préfixe étendu de $x$, autrement dit le [[Support d'un itemset|support]] de l'itemset formé du préfixe et de $x$.

Le test $count_x \ge minsup$ décide de la suite :

- si le seuil est atteint, l'itemset est fréquent et l'algorithme l'écrit en sortie ;
- il construit alors l'arbre conditionnel $FP_x$ à partir de la seule base $D_x$, et relance le même traitement sur cet arbre avec le préfixe augmenté de $x$.

L'appel récursif étend ainsi le motif un item à la fois. Chaque niveau de récursion retire l'item courant de la base conditionnelle, si bien que la base et l'arbre décroissent strictement : l'énumération se termine sur des arbres vides, et aucun motif n'est produit deux fois.

# Remarque

Le parcours récursif des bases conditionnelles est le mécanisme qui remplace la génération de candidats de l'[[Algorithme Apriori]] : le comptage se fait une fois pour toutes sur les chemins de l'arbre au lieu d'être refait sur la base pour chaque candidat, ce qui vaut à l'approche de la [[Principe de la croissance de motifs FP-growth|croissance de motifs]] son gain d'un ordre de grandeur en temps de calcul. Ce gain se lit sur les courbes des [[Temps d'exécution comparés des algorithmes]].

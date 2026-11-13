#dmv-frequent_itemsets_mining

# Interprétation

L'analyse du panier de la ménagère (*market basket analysis*) porte sur les données de transactions d'un supermarché.
Chaque transaction est le « panier » d'un client : l'ensemble des articles qu'il a achetés lors d'un même passage en caisse, c'est-à-dire un [[Items, itemsets et base de transactions|itemset]] de la base.

L'objectif est de déterminer quels articles sont souvent achetés ensemble, donc de dégager les [[Itemset fréquent|itemsets fréquents]] et les [[Règle d'association et confiance|règles d'association]] qui en découlent.

Applications directes :

- placement des produits dans les rayons ;
- vente croisée (*cross selling*), c'est-à-dire la suggestion d'autres produits au client ;
- promotions, en regroupant les articles achetés conjointement.

# Exemple

Les clients achètent souvent ensemble le pain, le chocolat et le beurre : `{pain, chocolat, beurre}` est un itemset fréquent.
Un achat de pain hamburger et de tomates s'accompagne fréquemment d'un achat de steak, ce qui s'écrit comme la règle `{pain hamburger, tomate} → {steak}`.

L'itemset le plus célèbre reste `{bière, couches}` : il a été trouvé dans une chaîne de supermarchés américains, et une étude plus poussée a montré que ces deux articles s'achètent surtout le vendredi soir.

# Remarque

L'analyse du panier est le cadre d'application typique de la [[Règle d'association et confiance]] : elle fixe les objets (transactions, items) sur lesquels se mesurent le support d'un itemset et la confiance d'une règle.
Le passage des transactions aux motifs se fait par le [[Calcul des règles d'association en deux étapes]], d'abord les itemsets fréquents, puis les règles de confiance suffisante.

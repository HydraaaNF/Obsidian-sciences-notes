#dmv-frequent_itemsets_mining

# Interprétation

FP-growth (Frequent Pattern Growth, croissance de motifs) calcule les [[Itemset fréquent|itemsets fréquents]] sans jamais énumérer de candidats, en s'appuyant sur trois idées :

- **aucune génération de candidats** : contrairement à l'[[Algorithme Apriori]], la méthode ne fabrique pas d'itemsets à tester puis à élaguer, elle lit les motifs directement dans une structure qui résume la base ;
- **compression de la base** en un [[Arbre FP]] (Frequent Pattern Tree), un arbre de préfixes étendu qui représente les transactions et les itemsets fréquents dans un espace réduit ;
- **traitement récursif de bases conditionnelles** : l'arbre est découpé en sous-bases associées à un préfixe d'items, et le même traitement y est relancé, ce qui développe les motifs par extension successive de leur préfixe.

L'approche se place ainsi en alternative directe au schéma générer et élaguer de l'[[Algorithme Apriori]], dont elle supprime l'étape la plus coûteuse.

# Propriétés

L'[[Arbre FP]] joue le rôle de représentant compact de la base et des motifs :

- il est construit à partir des transactions, comme un arbre de préfixes, avec en plus des liens entre branches pour un même item ;
- les itemsets fréquents réduits à un seul item se lisent directement dans l'arbre, leur support étant porté par les compteurs de nœuds ;
- sa structure est à la fois **horizontale**, par la disposition en arbre de préfixes, et **verticale**, par les chaînes de liens qui relient entre eux les nœuds d'un même item.

# Remarque

Le gain apporté par la croissance de motifs est un **ordre de grandeur** en temps de calcul face à l'[[Algorithme Apriori]] : l'absence de candidats et la compression de la base suppriment les parcours répétés de la base qu'exige le comptage de chaque candidat.

La [[Limites de l'approche brute force|génération exhaustive]] des itemsets reste l'arrière-plan que l'approche évite, et le détail du parcours récursif de l'arbre est donné par l'[[Algorithme FP-growth]].

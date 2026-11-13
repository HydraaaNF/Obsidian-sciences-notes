#dmv-frequent_itemsets_mining

# Interprétation

Deux familles d'algorithmes énumèrent les [[Itemsets fréquents fermés|itemsets fermés]] fréquents, et elles s'opposent par la mémoire qu'elles exigent.

Méthode à candidats, celle des premiers algorithmes (Closet, Charm, etc.) :

- on tente de calculer le plus grand nombre possible d'itemsets fréquents **non** fermés ;
- ou bien on procède par extension par fermeture : on ajoute un item à un itemset fermé fréquent déjà obtenu, puis on prend la fermeture du résultat ;
- dans les deux cas, l'algorithme doit garder en mémoire tous les itemsets fermés fréquents trouvés jusque-là.

Recherche inverse, celle de [[Recherche inverse des itemsets fermés|LCM]] :

- l'énumération est un parcours en profondeur, donc aucune mémoire globale n'est nécessaire ;
- le temps de calcul est rapide et la mémoire utilisée faible.

# Propriétés

Le coût des deux familles se sépare nettement :

- méthode à candidats : elle a besoin de beaucoup de mémoire pendant l'exécution, puisque l'ensemble des fermés déjà trouvés doit rester disponible tout du long ;
- recherche inverse : aucune mémoire globale n'est mobilisée, l'empreinte mémoire reste donc faible quel que soit le nombre d'itemsets fermés fréquents découverts.

# Remarque

La recherche inverse obtient donc le même résultat que la méthode à candidats sans jamais mémoriser l'ensemble des fermés déjà trouvés : le temps de calcul est rapide et l'usage mémoire faible, là où la méthode à candidats demande beaucoup de mémoire pendant l'exécution. Voir [[Calcul des itemsets fermés]] pour les voies d'énumération dont ces variantes relèvent, [[Algorithme LCM]] pour la mise en œuvre de la recherche inverse, et [[Fermeture d'un itemset et extension par fermeture]] pour l'opération d'extension par fermeture que les deux familles utilisent.

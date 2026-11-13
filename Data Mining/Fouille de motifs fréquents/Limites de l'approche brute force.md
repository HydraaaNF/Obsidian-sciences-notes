#dmv-frequent_itemsets_mining

# Algorithme

L'approche brute force pour calculer les [[Itemset fréquent|itemsets fréquents]] est la méthode **générer et tester** :

- générer des itemsets au hasard parmi tous les itemsets possibles ;
- calculer le support de chacun d'eux ;
- ne retenir que ceux dont le support atteint $minsup$.

# Interprétation

La méthode est correcte mais bute sur le nombre d'itemsets à examiner, qui croît de façon exponentielle avec le nombre d'items :

- un ensemble de $n$ items possède $2^n$ sous-ensembles, donc $2^n$ itemsets possibles (itemset vide compris) ;
- pour $1000$ items, cela fait $2^{1000}$ itemsets candidats, un nombre à plus de 300 chiffres ;
- chaque candidat exige en outre le parcours de la base pour calculer son support.

Le problème est donc hautement combinatoire et l'approche est **infaisable en pratique**.

# Remarque

L'énumération exhaustive ignore une information décisive : si un itemset n'est pas fréquent, aucun de ses sur-ensembles ne l'est, ce qui rend inutile l'examen de toute une partie de l'espace de recherche (voir la [[Propriété d'anti-monotonie du support]]).

C'est précisément ce que met à profit l'[[Algorithme Apriori]], qui engendre les candidats niveau par niveau à partir des seuls itemsets fréquents de la taille précédente au lieu de parcourir tous les itemsets possibles ; l'[[Complexité de l'algorithme Apriori]] conserve toutefois un pire cas exponentiel en le nombre d'items.

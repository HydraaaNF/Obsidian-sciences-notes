#dmv-sequence_mining

# Propriétés

La recherche exhaustive des itemsets d'une [[Items, itemsets et base de transactions|base de transactions]] parcourt un espace de recherche dont la taille est exponentielle en le nombre d'items distincts :

$$O\!\left(2^{\#\text{items}}\right)$$

L'[[Extension de la fouille de motifs aux données structurées|extension aux données structurées]] ne se contente pas de rendre ce dénombrement plus coûteux : l'espace de recherche peut devenir exponentiellement plus grand, et les valeurs précises de ce coût dépendent du problème traité.

L'écart se lit dans l'[[Espace de recherche des motifs séquentiels|espace de recherche]] des [[Motif séquentiel|motifs séquentiels]], rangé en niveaux de taille croissante. Sur un alphabet de quatre items, le premier niveau porte les quatre items A, B, C et D. Le deuxième niveau porte les séquences de deux items, dont AA, (AB), AB, BB, BC, (BC), A C, BD, A D et CD. Le troisième niveau porte les séquences de trois items, dont AAA, A(AB), AAB, A B C, A B D, BCD et ACD. Les niveaux continuent ainsi indéfiniment.

# Interprétation

Le contraste entre les deux familles de motifs tient à ce que chaque niveau de l'arbre énumère :

- pour les itemsets, les parties de l'ensemble des items : un item figure ou non dans un itemset, sans ordre ni répétition, ce qui ramène le niveau $k$ aux seuls itemsets de taille $k$ et l'arbre entier à $2^{\#\text{items}}$ nœuds ;
- pour les séquences, les suites d'éléments : un élément peut se répéter (AA) et l'ordre compte ((AB) n'est pas AB), si bien que chaque niveau rebranche sur l'alphabet entier et que le nombre de nœuds croît beaucoup plus vite.

Un arbre, un graphe ou une séquence n'énumèrent donc pas les mêmes objets, et le coût de leur fouille ne s'exprime pas par une formule unique : il dépend de la structure des données visée, de la définition d'inclusion retenue et des contraintes imposées aux motifs.

# Remarque

Le caractère exponentiel ne vient pas d'un algorithme particulier mais de l'énumération exhaustive elle-même. Les approches par génération et élagage combattent cette croissance en n'engendrant que les candidats dont les sous-motifs sont déjà fréquents, au prix d'un nombre d'itérations qui reste proportionnel à la profondeur de l'arbre ; voir [[Limites des approches générer et élaguer]].

Sur une base de transactions, le coût de cette stratégie est majoré par $O(m \cdot 2^{n})$ pour $m$ transactions et $n$ items ; voir [[Complexité de l'algorithme Apriori]].

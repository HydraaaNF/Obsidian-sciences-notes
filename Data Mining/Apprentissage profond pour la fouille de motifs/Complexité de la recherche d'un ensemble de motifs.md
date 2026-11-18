#dmv-pattern_mining_vs_deep_learning

# Propriétés

Un [[Ensemble de motifs]] réunit plusieurs motifs, et chaque motif est lui-même un sous-ensemble de l'ensemble des items $I$. Le nombre de motifs possibles vaut donc $2^{|I|}$, et un ensemble de motifs en choisit un sous-ensemble, si bien que le nombre d'ensembles de motifs possibles vaut :

$$2^{2^{|I|}}$$

Le nombre de candidats croît ainsi de façon doublement exponentielle avec le nombre d'items, et la recherche d'un ensemble de motifs a une complexité en temps doublement exponentielle.

Si la taille d'un ensemble recherché est bornée par $k$, l'énumération ne porte plus que sur les ensembles d'au plus $k$ motifs, soit :

$$\sum_{i \le k} \binom{2^{|I|}}{i}$$

candidats. Pour $k$ fixé, cette somme est dominée par son terme d'indice $k$ et vaut de l'ordre de $2^{k\,|I|}$ : l'exponentiation redevient simple, avec un exposant proportionnel au produit $k\,|I|$.

# Interprétation

La recherche d'un ensemble de motifs combine deux niveaux d'énumération : les motifs, sous-ensembles de $I$, puis les collections de motifs. Le premier niveau est l'explosion combinatoire décrite dans [[Limites des itemsets fréquents]], où abaisser le seuil de support démultiplie le nombre d'[[Itemset fréquent|itemsets fréquents]] à examiner ; le second niveau s'y ajoute, puisqu'il faut choisir une collection parmi les $2^{2^{|I|}}$ possibles.

Les algorithmes de l'état de l'art reposent sur des heuristiques pour explorer cet espace. Sur des [[Données de polymorphismes nucléotidiques simples|données de polymorphismes nucléotidiques simples]], qui comptent de 100 000 à 1 million d'items et sont denses, ils ne passent pas du tout à l'échelle.

# Remarque

Un ensemble de motifs est par définition un petit ensemble, qui capture les structures principales des données : le problème ne demande donc pas d'énumérer les $2^{2^{|I|}}$ ensembles, mais d'en trouver un de taille bornée. Cette restriction change l'ordre de grandeur : borner la taille par $k$ ramène l'espace à $2^{k\,|I|}$ candidats, exponentiel simple, tandis que le double exponentiel ne décrit que l'énumération de tous les ensembles, sans borne de taille. Pour $|I| = 10^5$, même avec $k = 5$, cela laisse encore de l'ordre de $2^{5 \times 10^5}$ candidats, hors de portée d'une énumération exhaustive : l'explosion reste considérable, mais elle n'est plus doublement exponentielle.

Le second niveau d'exponentiation a pour base le nombre de motifs, $2^{|I|}$, et non le nombre d'items lui-même : $|I|$ intervient donc deux fois, une fois dans le nombre de motifs, une fois dans le choix de la collection. C'est ce qui distingue la recherche d'un ensemble de motifs de la simple énumération des itemsets, dont l'espace reste en $2^{|I|}$.

Cet espace doublement exponentiel est aussi celui des tables de codes, chaque ensemble de motifs se réalisant en au moins une table : voir la [[Recherche de la table de codes optimale]].

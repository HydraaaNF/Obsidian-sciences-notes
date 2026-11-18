#dmv-pattern_mining_with_information_theory

# Définition

La taille totale d'un modèle et des données encodées avec ce modèle, pour une base $D$ et une [[Table de codes]] $CT$, est la somme de deux longueurs de description :

$$L(D, CT) = L(CT \mid D) + L(D \mid CT)$$

Le premier terme est la longueur de description du modèle, c'est-à-dire de la table de codes, donnée par la [[Longueur de description d'une table de codes]] :

$$L(CT \mid D) = \sum_{c \in CT : usage(c) \neq 0} \left( L(c \mid ST) + L(c \mid CT) \right)$$

Le second terme est la longueur de description des données encodées avec le modèle, donnée par la [[Longueur de description d'une base encodée]] :

$$L(D \mid CT) = \sum_{t \in D} L(t \mid CT)$$

C'est la mesure MDL que l'on cherche à minimiser.

# Interprétation

La table de codes joue le rôle du modèle $M$ et la base encodée le rôle des données vues à travers lui. Les deux termes se déplacent en sens inverse :

- enrichir la table, c'est allonger $L(CT \mid D)$, puisqu'une entrée de plus doit être décrite, avec son itemset et son code,
- enrichir la table, c'est aussi raccourcir $L(D \mid CT)$, puisqu'une entrée longue couvre d'un seul code ce que plusieurs singletons couvraient auparavant.

Le minimum de la somme arbitre entre ces deux mouvements : une table réduite aux singletons décrit un modèle très court mais des transactions chères, une table très riche fait l'inverse. C'est l'application à la [[Table de codes]] du [[Compromis entre longueur du modèle et longueur des données]].

Ce qui compte est la comparaison de deux tables construites pour la même base : c'est elle qui décide d'accepter ou de rejeter une entrée, pas la valeur de la somme prise isolément. Les deux termes sont mesurés dans la même unité, les bits produits par la [[Probabilité et longueur optimale d'un code|longueur optimale d'un code]], ce qui autorise leur addition.

# Remarque

La somme ne se décompose pas entrée par entrée : ajouter un itemset à la table change les usages, donc les longueurs de code de plusieurs autres entrées, et le gain d'une entrée ne se lit pas isolément. C'est précisément ce couplage qui rend la [[Recherche de la table de codes optimale]] difficile, et qui conduit l'[[Algorithme KRIMP]] à comparer globalement la table courante et la table augmentée d'un candidat.

Le minimum de $L(D, CT)$ est l'approximation praticable de la [[Complexité de Kolmogorov]] : là où la complexité de Kolmogorov demande le plus court programme générant les données, la taille totale se restreint aux modèles exprimables comme tables de codes, ce qui rend la quantité calculable pour une table donnée.

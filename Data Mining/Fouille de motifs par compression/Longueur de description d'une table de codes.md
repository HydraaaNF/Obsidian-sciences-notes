#dmv-pattern_mining_with_information_theory
# Définition

La longueur de description d'une [[Table de codes]] $CT$ au regard des données $D$, notée $L(CT \mid D)$, est la somme des longueurs nécessaires pour décrire chacune de ses entrées utilisées :

$$L(CT \mid D) = \sum_{c \in CT : usage(c) \neq 0} \left( L(c \mid ST) + L(c \mid CT) \right)$$

Chaque entrée d'usage non nul est donc décrite en deux parties : son itemset d'un côté, son code de l'autre.

# Interprétation

La première partie, $L(c \mid ST)$, mesure la longueur de l'itemset telle qu'elle s'encode avec le modèle d'indépendance, c'est-à-dire avec la [[Table de codes standard]]. Cette table ne dépend que des données, jamais du modèle construit : elle fournit donc une unité de mesure fixe, indépendante de $CT$, pour chiffrer la complexité d'un itemset.

La seconde partie, $L(c \mid CT)$, mesure la longueur du code affecté à l'entrée, calculée à partir de son usage selon la [[Probabilité et longueur optimale d'un code|longueur optimale]] : plus une entrée est utilisée, plus son code est court.

La taille d'une table de codes se lit ainsi comme la longueur de la colonne de gauche (les itemsets, décrits par l'indépendance) augmentée de la longueur de la colonne de droite (les codes, déterminés par les usages).

# Remarque

Seules les entrées d'usage non nul sont comptées : une entrée jamais utilisée pour couvrir une transaction n'ajoute rien à $L(CT \mid D)$. La taille d'une table ne mesure donc pas le nombre de lignes qu'elle affiche, mais la quantité d'information nécessaire pour décrire celles qui servent réellement.

Cette longueur ne suffit pas à juger une table de codes : une table très riche réduit la longueur des données encodées mais allonge la description du modèle. C'est la somme des deux termes, la [[Taille totale d'un modèle et des données encodées]], que la recherche du meilleur modèle minimise.

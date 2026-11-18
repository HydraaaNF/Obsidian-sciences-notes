#dmv-pattern_mining_with_information_theory
# Définition

Le modèle d'une [[Table de codes pour séquences d'événements|table de codes de séquences]] se décrit à son tour. La longueur de description d'un motif $X$ de la table est

$$L(X, CT) = L_{\mathbb{N}}(|X|) + L_{\mathbb{N}}(gaps(X) + 1) + \sum_{x \in X} L(code_p(x \mid ST))$$

La longueur de description de la table, pour un alphabet $\Omega$ et un ensemble $\mathcal{P}$ de motifs, est

$$L(CT \mid C) = L_{\mathbb{N}}(|\Omega|) + L_U(\|D\|, |\Omega|) + L_{\mathbb{N}}(|\mathcal{P}| + 1) + L_{\mathbb{N}}(usage(\mathcal{P}) + 1) + L_U(usage(\mathcal{P}), |\mathcal{P}|) + \sum_{X \in \mathcal{P}} L(X, CT)$$

# Interprétation

Un motif se décrit en trois parties : sa taille, son nombre de trous augmenté de un, puis ses événements, chacun encodé avec le code que lui attribue la [[Table de codes standard]] $ST$. Le recours à $ST$ mesure la complexité du motif avec un modèle d'indépendance qui ne dépend que des données, exactement comme la longueur $L(c \mid ST)$ d'une entrée de [[Table de codes|table de codes]] d'itemsets.

La table elle-même ajoute les quantités nécessaires pour la reconstruire : la taille de l'alphabet, le nombre de motifs, l'usage total des motifs, puis la description de chacun d'eux. Les termes en $L_U$ chiffrent les choix structurels de la table, et l'argument de chacun indique quelles quantités y sont combinées.

# Remarque

Cette description complète du modèle n'est pas nécessaire pour construire une table de codes : elle éclaire l'origine du terme de modèle, qui s'équilibre avec la [[Longueur de description d'une base de séquences]] dans l'objectif à minimiser.

Les motifs décrits par $\mathcal{P}$ s'ajoutent aux événements isolés de l'alphabet $\Omega$ : la table se lit comme l'alphabet augmenté des motifs non singletons retenus. C'est l'analogue, pour les séquences, de la [[Longueur de description d'une table de codes]] d'itemsets, où chaque entrée utilisée se décrit par son contenu et par son code.

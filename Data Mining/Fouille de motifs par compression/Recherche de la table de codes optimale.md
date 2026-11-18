#dmv-pattern_mining_with_information_theory

# Définition

La recherche de la table de codes optimale est le problème consistant à trouver, pour une base $D$ et un ensemble d'items $I$, la [[Table de codes]] $CT$ qui minimise la [[Taille totale d'un modèle et des données encodées]] :

$$CT^\star = \arg\min_{CT} L(D, CT)$$

Le critère est donc la longueur totale $L(CT \mid D) + L(D \mid CT)$, et non la seule longueur des données encodées.

# Interprétation

Le problème est simple à énoncer et sans solution directe, pour deux raisons qui se cumulent.

La première est quantitative : le nombre de tables de codes possibles est énorme. Une table est un ensemble d'[[Items, itemsets et base de transactions|itemsets]] muni de codes, et l'espace des tables contient au moins celui des [[Ensemble de motifs|ensembles de motifs]], qui compte $2^{2^{\lvert I \rvert}}$ candidats pour $\lvert I \rvert$ items : chaque ensemble de motifs se réalise en au moins une table de codes, en attribuant un code à chacun de ses itemsets.

La seconde est qualitative : aucune structure utile ne se laisse exploiter. La fonction objectif n'est pas additive sur les entrées de la table, puisqu'ajouter un itemset modifie les usages, donc les longueurs de code de plusieurs autres entrées. Il n'y a pas non plus d'ordre partiel sur les tables qui permettrait d'élaguer sûrement des candidats, ni de monotonie du gain selon la taille des itemsets ajoutés.

# Remarque

Faute de pouvoir énumérer, on recourt à des heuristiques, c'est-à-dire à des parcours guidés de l'espace des tables qui ne garantissent pas l'optimum mais produisent des tables de bonne qualité en un temps raisonnable. L'[[Algorithme KRIMP]] en est l'illustration pour les itemsets : il part de la [[Table de codes standard]] et ajoute les candidats un par un, en ne conservant que les ajouts qui font baisser $L(D, CT)$.

Le manque de structure est ce qui distingue ce problème de la fouille exhaustive d'itemsets : là où le [[Propriété d'anti-monotonie du support|support]] fournit un élagage sûr et permet d'énumérer tous les itemsets fréquents, la longueur totale ne fournit aucun élagage de ce type, et seuls des critères locaux, comme le tri des candidats par support décroissant, restent disponibles pour ordonner l'exploration.

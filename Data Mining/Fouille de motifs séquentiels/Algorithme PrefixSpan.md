#dmv-sequence_mining

# Définition

PrefixSpan est un algorithme de fouille de [[Motif séquentiel|motifs séquentiels]] qui relève de l'approche par croissance de motifs. Il ne se place pas dans la logique des [[Limites des approches générer et élaguer|approches générer puis élaguer]] : aucun candidat n'est engendré, les items fréquents sont extraits directement des [[Base projetée|bases projetées]], et la progression est celle d'un algorithme glouton.

L'idée directrice est d'utiliser un préfixe fréquent pour diviser l'[[Espace de recherche des motifs séquentiels|espace de recherche]] et calculer les bases projetées associées, afin de ne chercher que les séquences pertinentes. Les projections s'obtiennent en prélevant pour chaque [[Base de séquences|séquence de la base]] le [[Suffixe d'une séquence|suffixe]] qui subsiste une fois le préfixe consommé.

# Algorithme

L'algorithme informel se déroule en trois étapes, les étapes 2 et 3 étant reprises tant que de nouveaux préfixes apparaissent.

Étape 1 : extraction des 1-séquences fréquentes, par exemple $\langle a\rangle$, $\langle b\rangle$, $\langle c\rangle$, $\langle d\rangle$, $\langle e\rangle$, $\langle f\rangle$, $\langle g\rangle$.

L'ensemble des motifs séquentiels se trouve ainsi partitionné en sept sous-ensembles, selon le premier item du motif :

- ceux qui commencent par $\langle a\rangle$ ;
- ceux qui commencent par $\langle b\rangle$ ;
- ceux qui commencent par $\langle c\rangle$ ;
- ceux qui commencent par $\langle d\rangle$ ;
- ceux qui commencent par $\langle e\rangle$ ;
- ceux qui commencent par $\langle f\rangle$ ;
- ceux qui commencent par $\langle g\rangle$.

Étape 2 : calcul de la base projetée de chaque préfixe.

Étape 3 : pour chaque préfixe, calcul des candidats à être une [[Extensions d'une séquence|extension]]. Les candidats fréquents sont ajoutés et l'extension devient un nouveau préfixe, puis on revient à l'étape 2.

Fin : plus aucun préfixe ne peut être engendré.

# Remarque

L'algorithme tire trois avantages de ce principe :

- aucune génération de candidats, donc aucun candidat non pertinent à élaguer ;
- la base projetée rétrécit à chaque étape, le préfixe consommé disparaissant des séquences ;
- l'étape la plus coûteuse est la construction de la base projetée, coût que les [[Pseudo-projection|pseudo-projections]] réduisent en remplaçant la copie des séquences par un pointeur et un offset.

Par rapport à l'[[Algorithme GSP]], PrefixSpan est la variante par croissance de motifs : au lieu d'engendrer des candidats pour les évaluer ensuite, il extrait les items fréquents directement des bases projetées, ce qui le soustrait aux limites des approches générer puis élaguer. Le principe est parallèle à celui de [[Principe de la croissance de motifs FP-growth|FP-growth]] pour les itemsets fréquents : plutôt que d'énumérer des candidats, on fait croître des motifs à partir de préfixes fréquents, l'arbre de préfixes jouant pour les itemsets le rôle que la base projetée joue pour les séquences.

La sortie de PrefixSpan rassemble tous les motifs fréquents. L'[[Algorithme CloSpan]] en est l'extension pour le calcul des seuls [[Motif séquentiel clos|motifs séquentiels clos]] : il conserve la génération des motifs fréquents et y ajoute un post-élagage des séquences non closes.

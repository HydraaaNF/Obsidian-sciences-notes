#adm-8

# Définition

Une fonction de trait associe à un couple formé d'une observation $x$ et d'une étiquette $y$ une valeur réelle ou binaire :

$$f_j : X \times Y \to \mathbb{R} \text{ ou } \{0, 1\}$$

Lorsqu'elle est binaire, elle vaut $1$ quand le couple $(x, y)$ présente le fait décrit et $0$ sinon : c'est l'indicatrice d'un fait observé sur les données.

# Modèle

Un jeu de traits n'est pas énuméré trait par trait : il est décrit par des gabarits, c'est-à-dire des classes de fonctions de traits dont chaque membre est instancié sur les données. Les traits prennent souvent la forme d'un produit :

$$f_j(x, y) = A_a(x) B_b(y)$$

où $A_a$ et $B_b$ sont binaires. Le produit vaut alors $1$ si et seulement si $A_a(x) = 1$ et $B_b(y) = 1$ : $f_j$ est l'indicatrice d'une conjonction entre un état (une propriété de l'étiquette) et un fait observé (une propriété de l'observation). La forme concrète de ces gabarits est décrite dans [[Gabarits de traits et annotation BIO]].

# Propriétés

- Un trait pour séquences peut être propre à une position donnée, ou être sommé sur toutes les positions de la séquence.
- Il peut porter sur une seule observation $x_s$ à la position $s$, ou sur un ensemble d'observations allant jusqu'à $x$ tout entier.
- Il dépend d'au plus deux étiquettes voisines, jamais de $y$ globalement : c'est l'analogue de la [[Propriété de Markov]] dans un [[Modèle de Markov caché]], et la somme sur les positions qui en résulte est décrite dans [[Décomposition positionnelle des fonctions de traits]].
- Le jeu de traits est fixé une fois pour toutes, indépendamment de la longueur de la séquence : allonger la séquence ajoute des positions à parcourir, pas de nouveaux traits.
- Le décodage, c'est-à-dire l'inférence de la séquence d'étiquettes la plus probable, reste tractable, ce que permet précisément la forme positionnelle ci-dessus (voir [[Champ aléatoire conditionnel à chaîne linéaire]] et [[Décodage d'un champ aléatoire conditionnel à chaîne linéaire]]).
- Rien n'interdit à plusieurs traits de se chevaucher : un même couple $(x, y)$ peut vérifier simultanément un nombre quelconque d'entre eux.

# Exemple

Trois indicateurs portant sur un mot $x$ :

- $A_1(x) = \mathbb{1}[x \text{ commence par une majuscule}]$ ;
- $A_2(x) = \mathbb{1}[x \text{ commence par la lettre G}]$ ;
- $A_3(x) = \mathbb{1}[x \text{ a 6 lettres}]$.

Ces traits se chevauchent : un mot comme « Gaston » les vérifie tous les trois, « Paris » ne vérifie que le premier, « gare » aucun. Le chevauchement est arbitraire, aucune structure n'impose aux traits d'être disjoints.

Sur une séquence, les mêmes indicateurs s'appliquent position par position et peuvent porter sur des mots voisins, comme le montrent les exemples d'[[Étiquetage morphosyntaxique par fonctions de traits]].

# Remarque

Des indicateurs portant sur un mot isolé ne suffisent pas dès que la décision dépend d'une séquence : il faut des traits séquentiels, qui regardent les positions voisines, et un modèle dont le décodage reste tractable. C'est ce que réalise le [[Champ aléatoire conditionnel à chaîne linéaire|cadre conditionnel à chaîne linéaire]].

Les traits décrits ici généralisent ceux de [[Fonctions de traits d'un exemple de traduction]] : dans cet exemple chaque trait était l'indicatrice d'une propriété de la seule étiquette $y$, sans observation, et la distribution n'était pas conditionnée ; ici $A_a$ porte sur l'observation et $B_b$ sur l'étiquette, ce qui permet de conditionner sur un contexte et de traiter des séquences entières.

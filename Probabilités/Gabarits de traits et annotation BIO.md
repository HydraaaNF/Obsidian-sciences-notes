# Définition

En étiquetage de séquences, les [[Fonctions de traits pour les séquences|fonctions de traits]] ne sont pas énumérées à la main : les boîtes à outils les engendrent à partir de **gabarits** (en anglais *templates*), motifs textuels très concis dont chacun désigne une classe de traits.

Un gabarit repère une information des données par une écriture de la forme `%x[d,c]`, où les deux indices jouent des rôles distincts :

- `d` est un décalage de position par rapport à la position courante $k$ : `0` désigne la position $k$, `-2` la position $k-2$, `1` la position $k+1$ ;
- `c` est l'indice de la colonne lue à cette position, les colonnes étant numérotées à partir de `0`.

Un gabarit peut enchaîner plusieurs repères, séparés par `/` : il porte alors sur la conjonction des informations lues à ces repères. La boîte à outils instancie chaque gabarit à chaque position de la donnée, si bien qu'un même gabarit engendre autant de traits que la donnée compte de positions, sans que le nombre de gabarits dépende de la longueur des séquences.

# Exemple

Le cas d'usage classique est l'étiquetage morphosyntaxique de données déjà annotées en catégories grammaticales (POS), avec des étiquettes de chunks en annotation BIO. Les données se présentent en colonnes, par exemple :

| mot | catégorie grammaticale | étiquette |
|---|---|---|
| The | DT | B-NP |
| pen | NN | I-NP |
| is | VB | B-VP |
| a | DT | B-NP |

La colonne `0` contient le mot, la colonne `1` sa catégorie grammaticale. Un gabarit y lit alors :

| Gabarit | Information lue à la position $k$ |
|---|---|
| `U00:%x[-2,0]` | le mot $w_{k-2}$ |
| `U01:%x[-1,0]` | le mot $w_{k-1}$ |
| `U17:%x[1,0]/%x[1,1]` | le mot $w_{k+1}$ et sa catégorie $pos_{k+1}$ |
| `U18:%x[1,0]/%x[2,1]` | le mot $w_{k+1}$ et la catégorie $pos_{k+2}$ |
| `U20:%x[-2,1]/%x[-1,1]/%x[0,1]` | les catégories $pos_{k-2}$, $pos_{k-1}$ et $pos_{k}$ |

Chaque gabarit produit un trait pour chacune des positions de la donnée. À la position du mot « pen », le gabarit `U17:%x[1,0]/%x[1,1]` lit ainsi le mot suivant, « is », et sa catégorie, VB ; à la position du mot « is », le gabarit `U20:%x[-2,1]/%x[-1,1]/%x[0,1]` lit les catégories DT, NN et VB des trois positions correspondantes.

L'annotation BIO préfixe chaque étiquette de chunk par une lettre qui indique la place du mot dans le chunk : `B-` pour le premier mot d'un chunk (begin), `I-` pour un mot à l'intérieur (inside), et `O` pour un mot hors de tout chunk (outside). Ainsi `The DT B-NP` ouvre un groupe nominal, que `pen NN I-NP` prolonge, tandis que `is VB B-VP` ouvre un groupe verbal.

# Remarque

Les gabarits sont volontairement concis, au point d'être cryptiques, mais leur rôle est mécanique : chaque gabarit est une classe de fonctions de traits, et l'instanciation position par position fournit l'ensemble des traits du modèle. Le jeu de gabarits reste fixe quelle que soit la longueur de la séquence, ce qui donne un nombre de paramètres indépendant de cette longueur et rend le décodage tractable ; c'est le principe général des [[Fonctions de traits pour les séquences|fonctions de traits pour les séquences]], dont les gabarits ne sont qu'une syntaxe d'écriture.

Un gabarit porte sur l'observation seule : c'est la fonction de traits elle-même qui joint l'information observée à l'étiquette, en combinant un indicateur portant sur $x$ et un indicateur portant sur $y$. Le choix des gabarits fixe donc quelles régularités locales le modèle peut exploiter : mots voisins, catégories voisines, ou combinaisons des deux, comme dans l'[[Étiquetage morphosyntaxique par fonctions de traits]], dont les gabarits constituent la mise en œuvre outillée.

Ces traits engendrés par gabarits sont ceux que consomme le [[Champ aléatoire conditionnel à chaîne linéaire]], et leur forme locale, une contribution par position, est celle de la [[Décomposition positionnelle des fonctions de traits]].

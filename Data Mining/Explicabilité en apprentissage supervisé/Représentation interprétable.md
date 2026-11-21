#dmv-xai

# Définition

Une **représentation interprétable** décrit une instance par la présence ou l'absence d'éléments dont la signification est directement compréhensible par un humain, et non par les valeurs brutes de son signal d'entrée.

Chaque élément retenu fournit une coordonnée binaire : $1$ lorsqu'il est présent dans l'instance, $0$ lorsqu'il en est absent. Une instance se lit alors comme un vecteur de $0$ et de $1$, où chaque position désigne un composant identifiable.

# Exemple

Sur une image, les éléments sont des composants segmentés (superpixels) :

- l'image d'origine montre une grenouille tenant un fruit rouge ;
- sa version interprétable découpe la grenouille en parties segmentées et surlignées ;
- le masque de composants $[1\ 1\ 1\ 1\ 1\ \dots]$ décrit l'instance ;
- le masque $[0\ 1\ 0\ 1\ 0\ \dots]$ décrit un voisin où seuls certains composants subsistent ;
- le masque $[0\ 0\ 0\ 0\ 1\ \dots]$ en décrit un autre.

Sur un texte, les éléments sont les mots : la phrase « Livre monument : fabuleux livre, exhaustif, riche, documenté » se code par la présence de chacun de ses mots.

| livre | monument | fabuleux | exhaustif | riche | documenté |
|---|---|---|---|---|---|
| 1 | 1 | 1 | 1 | 1 | 1 |
| 1 | 0 | 1 | 0 | 1 | 1 |

La première ligne code l'instance, la seconde un voisin privé de « monument » et de « exhaustif ». Le même codage s'accompagne d'un affichage du texte où les mots retenus sont surlignés : `edu` dans l'adresse électronique, `NNTP Posting Host`, `have`.

La représentation alimente alors une contribution par élément interprétable. Un message est classé *atheism* avec la probabilité $0{,}59$ contre $0{,}41$ pour *christian*, et ses éléments contribuent à cette prédiction dans l'ordre décroissant :

| élément | contribution |
|---|---:|
| Posting | $0{,}16$ |
| Host | $0{,}13$ |
| NNTP | $0{,}10$ |
| edu | $0{,}05$ |
| have | $0{,}03$ |

Sur une série temporelle, les éléments sont des segments : la représentation note la présence ou l'absence d'un segment, et l'absence peut être modélisée de différentes façons :

- par interpolation linéaire entre les extrémités du segment retiré ;
- par une valeur constante sur toute la durée du segment.

La série initiale est tracée sur un axe des abscisses gradué de $0$ à $275$ et un axe des ordonnées allant de $-1$ à $1$ ; les deux variantes de l'absence se comparent à cette référence.

Des graphes de clustering stratégique (Espresso, Zucchini) figurent également parmi les supports pour lesquels une représentation interprétable est employée.

# Remarque

- La représentation interprétable n'est pas l'espace d'entrée du modèle : [[LIME]] y projette l'instance, y échantillonne des voisins autour de la cible, puis ajuste une approximation linéaire dans cet espace.
- La représentation sert une [[Explication locale]] : elle décrit une instance et son voisinage, non le comportement d'ensemble du modèle.
- Le choix des éléments conditionne l'[[Interprétabilité]] du résultat : pour qu'une explication ait un sens, ses éléments constitutifs doivent être compréhensibles.
- Une représentation apprise avec le modèle, par concepts ou prototypes, se distingue de celle construite après coup : voir les [[Explications par concepts et prototypes]].
- Les cartes de saillance produites par les [[Méthodes d'attribution par gradients]] forment une représentation de même nature, au niveau des pixels.
- Sur une série temporelle, les [[Shapelets]] jouent ce rôle de segments interprétables.

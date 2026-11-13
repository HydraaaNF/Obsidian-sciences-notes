#dmv-sequence_mining

# Interprétation

Les approches qui engendrent des candidats puis les élaguent, comme l'[[Algorithme GSP]] et, en [[Format vertical des transactions|format vertical]], l'[[Algorithme SPADE]], paient le principe générer puis élaguer par quatre coûts structurels :

- un grand nombre de candidats non pertinents est engendré ;
- la [[Base de séquences|base de séquences]] est lue plusieurs fois ;
- la mémoire est fortement sollicitée, la recherche par faisceau (beam search) l'étant particulièrement ;
- l'extraction de longues séquences n'est pas adaptée à ce type d'approche, le nombre de sous-séquences candidates croissant de façon exponentielle avec la longueur des motifs.

Ces coûts ne dépendent pas du détail de l'implémentation mais du principe même de l'énumération candidat par candidat : le volume de travail est gouverné par le nombre de motifs fréquents du niveau précédent et par la longueur des motifs visés. Le détail de l'engendrement et de l'élagage niveau par niveau est traité dans [[Génération et évaluation des candidats de GSP]], et la [[Anti-monotonie du support des motifs séquentiels|propriété d'anti-monotonie]] qui permet l'élagage ne supprime pas ces coûts, elle en limite seulement une partie.

# Exemple

Le premier coût se lit dès le deuxième niveau. À partir de $1000$ séquences fréquentes d'un item, le nombre de séquences candidates de deux items atteint :

$$1\,499\,500$$

Le quatrième coût apparaît avec la longueur : pour une séquence de $100$ items, le nombre de sous-séquences candidates vaut

$$2^{100} - 1 \approx 10^{30}$$

Un tel volume interdit d'énumérer les candidats un à un, quel que soit le soin apporté à l'élagage.

# Remarque

La valeur $1\,499\,500$ s'obtient en additionnant deux termes : $1000 \times 1000 = 1\,000\,000$ et $(1000 \times 999)/2 = 499\,500$. L'expression donnée sous forme de produit, $1000 \times 1000 \times (1000 \times 999)/2$, ne la redonne pas : son second signe est une addition et non une multiplication. L'ordre de grandeur du phénomène reste celui d'un nombre de candidats quadratique en le nombre de séquences fréquentes du niveau précédent.

Ces limites sont ce qui distingue l'approche générer puis élaguer de l'approche par croissance de motifs illustrée par l'[[Algorithme PrefixSpan]], qui parcourt le même [[Espace de recherche des motifs séquentiels|espace de recherche]] sans énumérer de candidats.

Le coût de la fouille dépend en outre de la structure des données : sur des données structurées, l'espace de recherche lui-même devient exponentiellement plus grand, voir [[Complexité de la fouille sur des données structurées]].

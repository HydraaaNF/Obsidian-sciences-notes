#dmv-frequent_itemsets_mining

# Définition

Un itemset $X$ est **fréquent** si son [[Support d'un itemset|support]] atteint le support minimum fixé :

$$\mathrm{support}(X) \ge minsup$$

où $minsup$ désigne le seuil de support minimum, exprimé en nombre de transactions ou en proportion de la base.

# Exemple

Base de six transactions :

| Transaction | Items achetés |
| :--- | :--- |
| 1 | bread, butter, chocolate, vine, pencil |
| 2 | bread, butter, chocolate, pencil |
| 3 | chocolate |
| 4 | butter, chocolate |
| 5 | bread, butter, chocolate, vine |
| 6 | bread, butter, chocolate |

Supports absolus des singletons :

- $\mathrm{support}(\{bread\}) = 4$
- $\mathrm{support}(\{butter\}) = 5$
- $\mathrm{support}(\{chocolate\}) = 6$
- $\mathrm{support}(\{vine\}) = 2$
- $\mathrm{support}(\{pencil\}) = 2$

Support de l'itemset $\{bread, butter, chocolate\}$ : il apparaît dans les transactions 1, 2, 5 et 6, soit $4/6 = 66\%$ de la base.

Avec $minsup = 3$ (support absolu), les itemsets fréquents de taille 1 sont $\{bread\}$, $\{butter\}$ et $\{chocolate\}$ ; $\{vine\}$ et $\{pencil\}$ ne sont pas fréquents. Avec $minsup = 2$, les cinq singletons sont fréquents, et $\{bread, butter, chocolate\}$ reste fréquent quel que soit le seuil retenu entre ces deux valeurs.

# Interprétation

Le seuil $minsup$ est un paramètre laissé à l'analyste : il fixe ce qu'on accepte de considérer comme un motif récurrent de la base. Sur les transactions d'un supermarché, cadre de l'[[Analyse du panier de la ménagère]], un itemset fréquent réunit des articles souvent achetés lors d'un même passage en caisse.

Il gouverne directement le volume de résultats :

- un $minsup$ élevé ne retient que les motifs très présents, donc peu nombreux ;
- un $minsup$ faible fait apparaître un très grand nombre d'itemsets fréquents, au prix d'un temps de calcul important et d'une forte redondance de l'information.

Sur une base de trois transactions $\{A, B, C, D\}$, $\{A, B, C\}$ et $\{A, B, C, E\}$ avec $minsup = 2$, on obtient déjà sept itemsets fréquents ($A$, $B$, $C$, $A B$, $A C$, $B C$, $A B C$), tous de support 3 et de même [[Support d'un itemset|tidlist]] $\{1, 2, 3\}$.

# Remarque

Tout sous-ensemble $I \subseteq A$ est un itemset (voir [[Items, itemsets et base de transactions]]) ; la fréquence est une propriété supplémentaire, relative au seuil $minsup$ et à la base considérée, que ne possède pas un itemset quelconque.

La fréquence se propage des sur-ensembles vers les sous-ensembles : si un itemset n'est pas fréquent, aucun de ses sur-ensembles n'est fréquent, ce qui est l'objet de la [[Propriété d'anti-monotonie du support]].

Le grand nombre d'itemsets fréquents produits à faible support motive des représentations condensées : les [[Itemsets fréquents fermés]] suppriment la redondance sans perdre les supports, tandis que les [[Itemsets fréquents maximaux]] la suppriment au prix d'une perte d'information, le support exact des itemsets non maximaux n'étant plus connu.

Cette définition est le cas particulier de l'[[Énoncé standard de la fouille de motifs]] obtenu en prenant pour langage de motifs les itemsets et pour ensemble de contraintes la seule contrainte de support minimal.

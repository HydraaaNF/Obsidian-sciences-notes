#dmv-frequent_itemsets_mining

# Définition

Un **itemset fréquent maximal** est un [[Itemset fréquent|itemset fréquent]] dont aucun sur-ensemble n'est fréquent. L'ensemble $MFI$ des itemsets fréquents maximaux d'une base s'écrit :

$$MFI = \{ I \in FI \mid \forall I' \supset I,\ I' \notin FI \}$$

où $FI$ désigne l'ensemble des [[Itemset fréquent|itemsets fréquents]] de la base pour le seuil $minsup$ retenu.

La condition porte sur les sur-ensembles stricts : un itemset fréquent qui admet au moins un sur-ensemble fréquent est écarté de $MFI$, et un seul sur-ensemble fréquent suffit à l'écarter.

# Propriétés

- $MFI$ est un sous-ensemble de $FI$ : tout itemset maximal est fréquent, l'inverse étant faux.
- Deux itemsets maximaux distincts ne sont jamais emboîtés : si $I$ et $I'$ appartiennent à $MFI$ et $I \subset I'$, alors $I$ possède le sur-ensemble fréquent $I'$ et n'est donc pas maximal.
- $MFI$ compte plusieurs ordres de grandeur d'itemsets de moins que $FI$ : la suppression des sur-ensembles fréquents élimine d'un coup toute la redondance accumulée dans les niveaux supérieurs du [[Treillis des itemsets|treillis]].
- Les ensembles d'itemsets s'ordonnent par inclusion, du plus condensé au plus détaillé : $MFI \subseteq CFI \subseteq FI$, où $CFI$ est l'ensemble des [[Itemsets fréquents fermés|itemsets fréquents fermés]].

# Interprétation

La recherche des itemsets maximaux peut être menée dans les deux sens du treillis :

- du bas vers le haut, en étendant des itemsets fréquents jusqu'à ne plus pouvoir les prolonger en restant fréquents ;
- du haut vers le bas, en partant d'itemsets aussi longs que possible et en les raccourcissant tant qu'ils restent infréquents, jusqu'au premier itemset fréquent, qui est alors maximal.

Cette double possibilité donne son nom à la [[Recherche bidirectionnelle des itemsets maximaux|recherche bidirectionnelle]] : l'algorithme Pincer-Search conjugue les deux directions en gardant trace des itemsets maximaux déjà rencontrés. L'algorithme Max-Miner explore quant à lui le treillis en élaguant des branches entières dès qu'un itemset maximal y est identifié.

Le gain est d'autant plus net que le seuil $minsup$ est bas : $FI$ devient alors bien plus grand que $MFI$.

# Remarque

La compression opérée par $MFI$ se paie d'une **perte d'information** : les itemsets non maximaux ne sont plus énumérés, et leur [[Support d'un itemset|support]] exact n'est plus connu, seule reste acquise la certitude qu'il atteint au moins $minsup$ puisque l'itemset est fréquent.

Cette perte est le motif de l'introduction des [[Itemsets fréquents fermés]] : ceux-ci conservent le support de chaque itemset en regroupant, dans une même classe d'équivalence, les itemsets qui partagent le même [[Support d'un itemset|tidlist]], tout en restant bien plus compacts que $FI$.

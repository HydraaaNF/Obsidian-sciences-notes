#dmv-frequent_itemsets_mining

# Définition

La **recherche bidirectionnelle** explore le [[Treillis des itemsets|treillis des itemsets]] par deux parcours menés de front, dans le but d'énumérer les [[Itemsets fréquents maximaux|itemsets fréquents maximaux]], c'est-à-dire les itemsets fréquents dont aucun sur-ensemble strict n'est fréquent.

- Le parcours **ascendant** (bottom-up) part des singletons, au niveau $k = 1$, et monte vers les itemsets de taille croissante.
- Le parcours **descendant** (top-down) part du sommet, l'itemset qui réunit tous les items, et descend vers les itemsets de taille décroissante.
- Chaque parcours entretient une **frontière** : les itemsets extrêmes qu'il a atteints, décidés du côté d'où il vient et encore ouverts de l'autre.
- Les deux frontières progressent l'une vers l'autre ; le **croisement** des frontières circonscrit la seule zone du treillis dont le statut reste à établir, et la recherche s'arrête quand cette zone est vide.

# Propriétés

- Un itemset infréquent atteint depuis le bas interdit tout son cône ascendant : par la [[Propriété d'anti-monotonie du support|propriété d'anti-monotonie du support]], aucun sur-ensemble ne peut être fréquent, et cette partie du treillis n'est plus considérée.
- Un itemset fréquent atteint depuis le haut autorise tout son cône descendant : tous ses sous-ensembles sont fréquents, sans qu'aucun d'eux ait à être testé.
- Un itemset déclaré fréquent par le parcours descendant est **maximal** : ses sur-ensembles ont été testés avant lui et jugés infréquents, si bien qu'il est livré comme résultat dès sa découverte.
- Un itemset déclaré fréquent par le parcours ascendant n'est maximal qu'une fois tous ses sur-ensembles écartés, donc après l'exploration de son cône ascendant.
- Chaque itemset maximal découvert depuis le haut retire de l'exploration un cône entier de sous-ensembles ; chaque itemset infréquent découvert depuis le bas retire un cône entier de sur-ensembles.
- Le croisement des deux frontières referme l'espace de recherche : au-dessus de la frontière descendante tout est décidé, en dessous de la frontière ascendante tout est décidé, et seule la bande intermédiaire demande encore des tests.

# Interprétation

Une exploration purement ascendante, comme celle de l'[[Algorithme Apriori|algorithme Apriori]], ne dispose que d'une seule source d'information : elle doit gravir le treillis niveau par niveau, tester tous les candidats de chaque niveau et ne reconnaître la maximalité d'un itemset qu'après avoir traité tous ses sur-ensembles. Le parcours descendant lui apporte l'information symétrique, lue sur les mêmes arêtes en sens inverse, et les deux sens se complètent selon la forme des données :

- Quand les itemsets fréquents sont longs et nombreux, le parcours descendant rencontre très tôt de grands itemsets fréquents, dont la fréquence acquiert d'avance toute la partie basse du treillis : l'essentiel de l'exploration est supprimé, et les itemsets maximaux sortent sans être reconstruits depuis les singletons.
- Quand les itemsets fréquents sont courts, le parcours ascendant écarte immédiatement les grands itemsets par l'infréquence de leurs sous-ensembles, là où un parcours descendant parti du sommet testerait une masse d'itemsets infréquents sans rien pouvoir couper d'utile.
- Le double sens couvre les deux régimes dans la même recherche : chaque frontière élague depuis son côté, et la zone intermédiaire se referme au lieu de rester à parcourir en entier.

# Exemple

Le treillis se lit de bas en haut : l'itemset vide en occupe le fond, les singletons forment le niveau $k = 1$, puis les niveaux $k = 2$, $k = 3$ et $k = 4$ s'élèvent jusqu'à l'itemset plein, qui réunit tous les items au sommet.

- Le parcours **descendant** part de l'itemset plein et gagne les niveaux inférieurs le long des arêtes ; sur un treillis dont les itemsets s'élèvent jusqu'au niveau $k = 4$, il reconnaît ses premiers itemsets maximaux aux itérations 2, 3 et 4.
- Le parcours **ascendant** part des singletons du niveau $k = 1$ et monte de niveau en niveau vers les itemsets plus grands ; dans le même déroulement, il reconnaît des itemsets maximaux aux itérations 3, 4 et 4.
- Chaque itemset maximal reconnu est retenu avec le rang de l'itération qui l'a trouvé, qu'il vienne du haut ou du bas.
- Un itemset maximal reconnu depuis le haut rend inutile l'examen de tout son cône de sous-ensembles : leur fréquence est acquise, si bien que la partie du treillis qui s'étend sous lui jusqu'au fond sort de l'espace de recherche.
- Les deux parcours se rejoignent au voisinage de la bande médiane : les itemsets maximaux se trouvent de part et d'autre de la ligne où les deux frontières se rencontrent, et seule la bande restée indécise demande encore des tests.

# Remarque

La recherche bidirectionnelle ne remplace pas l'exploration du [[Treillis des itemsets|treillis]] : elle la double, chaque parcours restant un parcours d'arêtes régi par l'anti-monotonie du support. Son intérêt tient à l'[[Propriété d'anti-monotonie du support|anti-monotonie du support]] le long des arêtes, qui rend l'information vraie dans les deux sens : un nœud fréquent atteste tous ses descendants, un nœud infréquent atteste tous ses ancêtres.

Elle ne se justifie que si l'on cherche les seuls [[Itemsets fréquents maximaux|itemsets maximaux]] : le parcours descendant écarte des sous-ensembles fréquents dont l'énumération complète serait nécessaire pour reconstituer tous les [[Itemset fréquent|itemsets fréquents]]. Voir aussi les [[Classes d'équivalence des itemsets|classes d'équivalence du treillis]], qui découpent le même espace de recherche par les tidsets plutôt que par les deux extrémités.

#dmv-sequence_mining

# Définition

Un [[Motif séquentiel|motif séquentiel]] s'allonge d'un item de deux manières, selon que cet item forme un nouvel itemset ou rejoint un itemset déjà présent.

**S-extension** : ajouter un itemset à la séquence.

$$\langle(a,b)(c)\rangle \rightarrow \langle(a,b)(c)(d)\rangle$$

**I-extension** : ajouter un item dans un itemset existant de la séquence.

$$\langle(a,b)(c)\rangle \rightarrow \langle(a,b)(c,d)\rangle$$

# Exemple

Sur un alphabet de six items $\{a, b, c, d, e, f\}$, les séquences de longueur 2 s'obtiennent en étendant une fois les séquences de longueur 1. Dans les tables suivantes, la concaténation note des itemsets successifs : $\langle ab\rangle$ est la séquence $\langle(a)(b)\rangle$, tandis que $\langle(ab)\rangle$ est la séquence réduite à l'itemset $\{a, b\}$.

S-extension : la ligne donne la séquence de départ, la colonne l'item ajouté dans un nouvel itemset.

| | $\langle a\rangle$ | $\langle b\rangle$ | $\langle c\rangle$ | $\langle d\rangle$ | $\langle e\rangle$ | $\langle f\rangle$ |
|---|---|---|---|---|---|---|
| $\langle a\rangle$ | $\langle(a)(a)\rangle$ | $\langle ab\rangle$ | $\langle ac\rangle$ | $\langle ad\rangle$ | $\langle ae\rangle$ | $\langle af\rangle$ |
| $\langle b\rangle$ | $\langle ba\rangle$ | $\langle bb\rangle$ | $\langle bc\rangle$ | $\langle bd\rangle$ | $\langle be\rangle$ | $\langle bf\rangle$ |
| $\langle c\rangle$ | $\langle ca\rangle$ | $\langle cb\rangle$ | $\langle cc\rangle$ | $\langle cd\rangle$ | $\langle ce\rangle$ | $\langle cf\rangle$ |
| $\langle d\rangle$ | $\langle da\rangle$ | $\langle db\rangle$ | $\langle dc\rangle$ | $\langle dd\rangle$ | $\langle de\rangle$ | $\langle df\rangle$ |
| $\langle e\rangle$ | $\langle ea\rangle$ | $\langle eb\rangle$ | $\langle ec\rangle$ | $\langle ed\rangle$ | $\langle ee\rangle$ | $\langle ef\rangle$ |
| $\langle f\rangle$ | $\langle fa\rangle$ | $\langle fb\rangle$ | $\langle fc\rangle$ | $\langle fd\rangle$ | $\langle fe\rangle$ | $\langle ff\rangle$ |

I-extension : l'item ajouté entre dans l'itemset de départ.

- depuis $\langle a\rangle$ : $\langle(ab)\rangle$, $\langle(ac)\rangle$, $\langle(ad)\rangle$, $\langle(ae)\rangle$, $\langle(af)\rangle$
- depuis $\langle b\rangle$ : $\langle(bc)\rangle$, $\langle(bd)\rangle$, $\langle(be)\rangle$, $\langle(bf)\rangle$
- depuis $\langle c\rangle$ : $\langle(cd)\rangle$, $\langle(ce)\rangle$, $\langle(cf)\rangle$
- depuis $\langle d\rangle$ : $\langle(de)\rangle$, $\langle(df)\rangle$
- depuis $\langle e\rangle$ : $\langle(ef)\rangle$
- depuis $\langle f\rangle$ : aucune

La table de I-extension ne remplit que le triangle strictement supérieur de la grille : l'itemset $\{a, b\}$ ne dépend pas de l'ordre de ses items, donc $\langle(ab)\rangle$ s'obtient aussi bien depuis $\langle a\rangle$ que depuis $\langle b\rangle$, et une seule des deux cases suffit. Les deux tables réunies fournissent les $36$ séquences de S-extension et les $15$ de I-extension, soit $51$ candidats de longueur 2.

# Remarque

Les deux extensions ajoutent exactement un item, ce qui range les séquences engendrées au niveau de longueur suivant : c'est ce qui organise l'[[Espace de recherche des motifs séquentiels|espace de recherche]] en arbre, chaque séquence ayant pour racine $\{\}$ et pour parent la séquence dont elle est une extension.

Un item peut se répéter dans une séquence : la case $\langle(a)(a)\rangle$ montre une S-extension par un item déjà présent, ce qui distingue radicalement l'espace séquentiel du [[Treillis des itemsets|treillis des itemsets]], où chaque item n'apparaît qu'une fois.

L'[[Algorithme GSP]] construit ses candidats de longueur $k+1$ en étendant par S-extension et I-extension les [[Motif séquentiel|motifs séquentiels]] fréquents de longueur $k$, puis les élague par [[Anti-monotonie du support des motifs séquentiels|anti-monotonie du support]] ; le déroulé de cet engendrement est décrit dans [[Génération et évaluation des candidats de GSP]].

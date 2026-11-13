#dmv-frequent_itemsets_mining

# Propriété

À itemset source fixé, la [[Règle d'association et confiance|confiance]] d'une règle est **anti-monotone** par rapport au nombre d'items de son conséquent : plus le conséquent contient d'items, plus la confiance est faible.

Soit $L$ un itemset et $a$ un sous-ensemble non vide de $L$, la règle considérée étant $a \to L \setminus a$. Sa confiance s'écrit, en reprenant la définition de la confiance et en remarquant que l'union des deux itemsets est $L$ :

$$c(a \to L \setminus a) = \frac{\mathrm{support}(L)}{\mathrm{support}(a)}$$

Le numérateur est constant pour toutes les règles issues de $L$ ; seule varie la taille de l'antécédent $a$, donc du conséquent $L \setminus a$.

# Exemple

Pour l'itemset $L = \{A, B, C, D\}$, les trois règles qui envoient un, deux puis trois items dans le conséquent vérifient :

$$c(ABC \to D) \ge c(AB \to CD) \ge c(A \to BCD)$$

Le conséquent passe de un à deux puis trois items, et la confiance ne peut que décroître.

# Démonstration

Soit $L$ un itemset et deux antécédents emboîtés $a' \subset a \subset L$, d'où des conséquents emboîtés en sens inverse, $L \setminus a \subset L \setminus a'$.

Par l'anti-monotonie du [[Support d'un itemset|support]], un sur-ensemble a un support inférieur ou égal à celui de ses sous-ensembles, donc :

$$\mathrm{support}(a') \ge \mathrm{support}(a)$$

Les deux règles issues de $L$ ont même numérateur $\mathrm{support}(L)$, d'où, en divisant par des dénominateurs ordonnés en sens inverse :

$$\frac{\mathrm{support}(L)}{\mathrm{support}(a')} \le \frac{\mathrm{support}(L)}{\mathrm{support}(a)}$$

C'est-à-dire :

$$c(a' \to L \setminus a') \le c(a \to L \setminus a)$$

La règle dont le conséquent est le plus gros, donc l'antécédent le plus petit, est la moins confiante.

# Interprétation

La propriété fournit un **élagage** lors de la génération des règles : si une règle dont le conséquent contient $m$ items n'atteint pas le seuil $minconf$, aucune règle de même itemset source dont le conséquent est un sur-ensemble de ces $m$ items ne peut l'atteindre non plus. Toute la branche correspondante est donc abandonnée sans calcul, ce qu'exploite l'[[Algorithme ap-genrules]] en supprimant de l'ensemble des conséquents candidats ceux qui échouent au test de confiance, puis en ne développant que les survivants.

# Remarque

L'anti-monotonie ne vaut qu'à itemset source fixé : elle compare les découpages d'un **même** itemset entre antécédent et conséquent. Entre itemsets différents, la confiance n'est ni monotone ni anti-monotone, comme le montre [[Monotonie de la confiance]] sur des règles emboîtées dont l'union change.

# Liens avec d'autres notions

L'[[Propriété d'anti-monotonie du support|anti-monotonie du support]], qui porte sur la fréquence d'un itemset et non sur une règle, fonde la démonstration précédente et sert le même but : restreindre l'espace exploré.

Les deux propriétés se succèdent dans le [[Calcul des règles d'association en deux étapes]] : l'anti-monotonie du support sélectionne en amont les [[Itemset fréquent|itemsets fréquents]], celle de la confiance élague en aval la [[Génération des règles d'association]].

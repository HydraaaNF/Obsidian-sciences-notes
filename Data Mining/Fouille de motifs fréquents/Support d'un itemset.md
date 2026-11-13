#dmv-frequent_itemsets_mining

# Définition

Soit $A = \{a_1, \dots, a_n\}$ une base d'items et $T = (t_1, \dots, t_m)$ une [[Items, itemsets et base de transactions|base de transactions]], chaque transaction $t_j$ étant un sous-ensemble de $A$, d'indice $\mathrm{tid}(t_j) = j$.

Le **support** d'un itemset $X \subseteq A$ est le nombre de transactions qui contiennent $X$ :

$$\mathrm{support}(X) = |\{j \mid X \subseteq t_j\}|$$

La **tidlist** de $X$ est la liste des identifiants des transactions (tids) qui contiennent $X$ :

$$\mathrm{tidlist}(X) = \{j \mid X \subseteq t_j\}$$

# Propriétés

Le support d'un itemset est le cardinal de sa tidlist :

$$\mathrm{support}(X) = |\mathrm{tidlist}(X)|$$

Il s'écrit sous deux formes :

- support absolu, le nombre de transactions, tel que défini ci-dessus ;
- support relatif, le rapport au nombre total de transactions : $s(X) = \dfrac{\mathrm{support}(X)}{m}$.

Les deux formes ne se confondent pas : un support absolu de $4$ sur une base de $6$ transactions correspond à un support relatif de $4/6 = 66\,\%$.

La tidlist d'une union d'itemsets s'obtient par intersection des tidlists, ce qui donne le support sans test d'inclusion :

$$\mathrm{tidlist}(I \cup J) = \mathrm{tidlist}(I) \cap \mathrm{tidlist}(J)$$

Cette identité est exploitée par le [[Format vertical des transactions]], voir [[Support par intersection de tidlists]].

# Exemple

Sur la base de six transactions suivante :

| Transaction | Items |
|---|---|
| 1 | bread, butter, chocolate, vine, pencil |
| 2 | bread, butter, chocolate, pencil |
| 3 | chocolate |
| 4 | butter, chocolate |
| 5 | bread, butter, chocolate, vine |
| 6 | bread, butter, chocolate |

L'itemset $\{bread, butter, chocolate\}$ est contenu dans les transactions $1$, $2$, $5$ et $6$ :

- $\mathrm{tidlist}(\{bread, butter, chocolate\}) = \{1, 2, 5, 6\}$ ;
- support absolu : $4$ ;
- support relatif : $4/6 = 66\,\%$.

L'itemset $\{bread, butter, chocolate\}$ est donc présent dans $4$ transactions sur $6$.

# Remarque

Un itemset dont le support atteint un seuil minimum $minsup$ est un [[Itemset fréquent]] : le support est la quantité que l'algorithme de fouille compare à ce seuil, et le choix entre support absolu et support relatif fixe l'unité de $minsup$.

Le support mesure la fréquence d'un itemset, pas la force d'une implication : la [[Règle d'association et confiance|confiance]] d'une règle s'obtient en rapportant le support de $X \cup Y$ à celui de $X$.

#dmv-frequent_itemsets_mining

# Propriétés

Soient $X$ et $Y$ deux [[Items, itemsets et base de transactions|itemsets]] tels que $X \subseteq Y$. Le [[Support d'un itemset|support]] décroît quand l'itemset grandit :

$$\mathrm{support}(Y) \le \mathrm{support}(X)$$

**Propriété d'anti-monotonie du support** (propriété d'Apriori) : si un itemset n'est pas [[Itemset fréquent|fréquent]], alors aucun de ses sur-ensembles n'est fréquent :

$$X \text{ non fréquent} \implies \forall\, Y \supseteq X,\ Y \text{ non fréquent}$$

Autrement dit, pour tout seuil $minsup$ :

$$\mathrm{support}(X) < minsup \implies \forall\, Y \supseteq X,\ \mathrm{support}(Y) < minsup$$

La forme équivalente par contraposée porte sur les itemsets fréquents : si un itemset est fréquent, alors tous ses sous-ensembles sont fréquents.

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

Avec $minsup = 3$ (support absolu), l'itemset $\{vine, pencil\}$ a pour support $1$ : il n'est pas fréquent. Aucun de ses sur-ensembles ne peut donc l'être, et en particulier $\{vine, pencil, chocolate\}$ n'est pas fréquent, son support valant lui aussi $1$.

Le raisonnement vaut pour tout sur-ensemble : un itemset qui contient à la fois $vine$ et $pencil$ n'est présent que dans les transactions qui contiennent déjà $\{vine, pencil\}$, donc dans au plus une transaction.

# Interprétation

La propriété transforme une condition sur les sur-ensembles en condition sur un seul itemset : pour décider qu'un itemset de grande taille est écarté, il suffit de constater qu'un de ses sous-ensembles ne franchit pas le seuil, sans compter son support ni le parcourir.

Elle permet ainsi d'élaguer le [[Treillis des itemsets]] : dès qu'un nœud n'est pas fréquent, tout le sous-arbre de ses sur-ensembles est écarté d'un bloc.

C'est le fondement de l'[[Algorithme Apriori]], qui explore le treillis niveau par niveau et n'étend que les itemsets fréquents. La [[Génération des candidats par apriori-gen|génération des candidats]] l'utilise dans son étape d'élagage : un candidat de taille $k$ est supprimé dès qu'un de ses $(k-1)$-sous-ensembles n'est pas fréquent.

L'élagage vaut aussi en parcours en profondeur, mais sous conditions. Sur l'exemple de la recherche en profondeur d'[[Algorithme Eclat|Eclat]], l'itemset $\{a, c, d, e\}$ peut être écarté sans calculer son support, parce que son sous-ensemble $\{c, d, e\}$ n'est pas fréquent. Eclat n'obtient ce résultat que si le parcours en profondeur de l'arbre de préfixes se fait de droite à gauche et si les supports déjà calculés sont conservés : le gain attendu est discuté, car il se paie en mémoire.

# Remarque

La propriété porte deux noms équivalents : propriété de fermeture descendante (downward closure), parce que la fréquence se conserve en descendant vers les sous-ensembles, et propriété d'anti-monotonie, parce qu'elle inverse le sens de variation du support par rapport à l'inclusion.

Elle ne dit rien de la fréquence des itemsets qui ne sont pas comparables par inclusion : deux itemsets de même taille peuvent avoir des supports très différents, et l'un être fréquent quand l'autre ne l'est pas.

Elle ne se transpose pas telle quelle à la [[Règle d'association et confiance|confiance]] : en général la confiance n'est ni monotone ni anti-monotone. Un énoncé analogue vaut seulement à itemset source fixé, où la confiance décroît quand le nombre d'items du conséquent augmente, ce qui fonde un autre élagage, décrit dans l'[[Anti-monotonie de la confiance selon la taille du conséquent]].

#dmv-frequent_itemsets_mining

# Définition

Une **règle d'association** est une implication entre deux itemsets disjoints d'une [[Items, itemsets et base de transactions|base de transactions]] :

$$X \to Y$$

La **confiance** de la règle est le rapport du [[Support d'un itemset|support]] de l'union des deux itemsets au support de l'antécédent :

$$c = \frac{\mathrm{support}(X \cup Y)}{\mathrm{support}(X)}$$

La règle est dite **valide** pour un seuil de confiance minimum $minconf$ lorsque :

$$c \ge minconf$$

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

Les itemsets $\{bread, butter, chocolate\}$ et $\{butter, chocolate\}$ sont présents dans $4$ et $5$ transactions respectivement, donc :

- $\{butter, chocolate\} \to \{bread\}$ a pour confiance $4/5 = 80\,\%$ ;
- $\{chocolate\} \to \{bread, butter\}$ a pour confiance $4/6 = 66\,\%$ ;
- $\{chocolate\} \to \{butter\}$ a pour confiance $5/6 = 83\,\%$.

Avec $minconf = 80\,\%$, les règles $\{butter, chocolate\} \to \{bread\}$ et $\{chocolate\} \to \{butter\}$ sont valides, alors que $\{chocolate\} \to \{bread, butter\}$ ne l'est pas.

# Interprétation

La confiance mesure la force de l'implication, là où le support mesure la fréquence : elle répond à la question « parmi les transactions qui contiennent $X$, quelle proportion contient aussi $Y$ ? ». Lue sur les tickets de caisse d'un supermarché, c'est-à-dire dans le cadre de l'[[Analyse du panier de la ménagère]], elle donne la proportion des paniers qui contiennent $X$ et contiennent aussi $Y$.

Deux règles obtenues en permutant antécédent et conséquent ne se valent pas : $\{butter, chocolate\} \to \{bread\}$ a une confiance de $80\,\%$, tandis que $\{bread\} \to \{butter, chocolate\}$ atteindrait $4/4 = 100\,\%$. La confiance n'est donc pas symétrique.

Les deux seuils jouent des rôles distincts : $minsup$ sélectionne les [[Itemset fréquent|itemsets fréquents]] et porte donc sur l'union $X \cup Y$ avant toute extraction de règle, $minconf$ filtre ensuite les règles tirées de ces itemsets. Le calcul se fait en deux étapes parce que la découverte des itemsets fréquents est très coûteuse en calcul, alors que partitionner un itemset déjà obtenu est bien plus rapide (voir [[Calcul des règles d'association en deux étapes]], détaillé par la [[Génération des règles d'association]]).

# Remarque

À la différence du support, qui décroît quand l'itemset grandit (tout sur-ensemble d'un itemset a un support inférieur ou égal, voir [[Propriété d'anti-monotonie du support]]), la confiance n'est ni monotone ni anti-monotone quand on passe d'un itemset à un sur-ensemble : une règle plus spécifique peut être meilleure qu'une règle plus générale, ce que détaille [[Monotonie de la confiance]].

En revanche, à itemset source fixé, la confiance ne peut que décroître quand le nombre d'items du conséquent augmente, propriété d'anti-monotonie exploitée pour élaguer la recherche de règles (voir [[Anti-monotonie de la confiance selon la taille du conséquent]]).

Une confiance de $100\,\%$ s'obtient dès que l'antécédent n'apparaît que dans des transactions contenant aussi le conséquent ; elle ne suppose aucune relation causale entre les itemsets, seulement une cooccurrence dans la base observée.

L'itemset $\{bread, butter, chocolate\}$ est vendu dans $4/6 = 66\,\%$ des transactions : la règle qui en partitionne les items peut avoir une confiance nettement supérieure à cette fréquence.

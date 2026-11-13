#dmv-frequent_itemsets_mining

# Exemple

**Support d'un itemset**

Une base de transactions décrit des achats :

| Transaction | Items achetés |
| :---: | :--- |
| 1 | bread, butter, chocolate, vine, pencil |
| 2 | bread, butter, chocolate, pencil |
| 3 | chocolate |
| 4 | butter, chocolate |
| 5 | bread, butter, chocolate, vine |
| 6 | bread, butter, chocolate |

Compléter le support de l'itemset $\{bread, butter, chocolate\}$, d'abord en valeur absolue, c'est-à-dire en nombre de transactions, puis en valeur relative.

**Confiance d'une règle à antécédent d'un item**

Sur la même base, compléter la confiance de la règle :

$$\{chocolate\} \to \{bread, butter\}$$

**Confiance d'une règle à antécédent de deux items**

Sur la même base, compléter la confiance de la règle :

$$\{butter, chocolate\} \to \{bread\}$$

**Nombre de règles d'un itemset de taille $k$**

Soit $F$ un itemset de taille $k$, c'est-à-dire $|F| = k$, dont on sait qu'il est fréquent. Une fois les itemsets fréquents obtenus, on veut en tirer des [[Règle d'association et confiance|règles d'association]] de confiance élevée.

Trois questions se posent :

- combien de règles possibles un tel itemset engendre-t-il ?
- quelle solution naïve permet de les calculer ?
- cette solution est-elle efficace ?

# Remarque

**Support de l'itemset**

L'itemset $\{bread, butter, chocolate\}$ est contenu dans les transactions $1$, $2$, $5$ et $6$, et dans aucune des transactions $3$ et $4$, qui ne contiennent pas les trois items à la fois. D'où le support absolu, qui est un nombre de transactions :

$$\mathrm{support}(\{bread, butter, chocolate\}) = 4$$

Le support relatif rapporte ce compte au nombre total de transactions de la base, qui vaut $6$ :

$$\frac{4}{6} \approx 66{,}7\,\%$$

**Confiance de $\{chocolate\} \to \{bread, butter\}$**

La [[Règle d'association et confiance|confiance]] d'une règle est le rapport du support de l'union au support de l'antécédent :

$$c = \frac{\mathrm{support}(X \cup Y)}{\mathrm{support}(X)}$$

L'union des deux itemsets redonne l'itemset $\{bread, butter, chocolate\}$, de support $4$. L'antécédent $\{chocolate\}$ est contenu dans les transactions $1$, $2$, $3$, $4$, $5$ et $6$, donc de support $6$. La confiance vaut donc :

$$c = \frac{4}{6} \approx 66{,}7\,\%$$

Deux tiers des paniers qui contiennent du chocolat contiennent aussi du pain et du beurre.

**Confiance de $\{butter, chocolate\} \to \{bread\}$**

Le numérateur reste le support de $\{bread, butter, chocolate\}$, soit $4$. L'antécédent $\{butter, chocolate\}$ est contenu dans les transactions $1$, $2$, $4$, $5$ et $6$, et manque dans la transaction $3$, qui ne contient que du chocolat : son support est $5$. La confiance vaut donc :

$$c = \frac{4}{5} = 80\,\%$$

Les deux règles ne se valent pas : la seconde, dont l'antécédent est plus spécifique, est plus confiante que la première, alors que les deux partagent le même numérateur. C'est l'illustration du fait que la confiance n'est pas monotone quand on passe d'un antécédent à un sur-ensemble (voir [[Monotonie de la confiance]]).

**Nombre de règles et coût de leur calcul**

Une règle issue de $F$ partitionne $F$ en un antécédent $X$ et un conséquent $Y = F \setminus X$, tous deux non vides. Les antécédents possibles sont donc les $2^{k}$ parties de $F$, à l'exclusion de $\varnothing$, qui donnerait la règle $\varnothing \to F$, et de $F$ lui-même, qui donnerait la règle $F \to \varnothing$. Le nombre de règles candidates d'un itemset de taille $k$ est ainsi :

$$N(k) = 2^{k} - 2$$

Quelques valeurs : $2$ règles pour $k = 2$, $6$ pour $k = 3$, $14$ pour $k = 4$, $30$ pour $k = 5$ et $1022$ pour $k = 10$.

La solution naïve consiste à énumérer ces $2^{k} - 2$ partitions et à calculer la confiance de chacune en allant chercher les deux supports nécessaires dans la base, par un parcours des transactions. Elle n'est pas efficace, pour deux raisons cumulées : le nombre de règles croît exponentiellement avec la taille de l'itemset, et chaque confiance demande le calcul d'un support qui n'est pas encore connu, alors que le support de l'union est le même pour toutes les règles issues de $F$.

La [[Génération des règles d'association|génération des règles]] évite ces calculs : partant des [[Itemset fréquent|itemsets fréquents]] et de leurs supports déjà calculés, elle lit chaque confiance comme le rapport de deux valeurs connues, puis élague à l'aide de l'[[Anti-monotonie de la confiance selon la taille du conséquent|anti-monotonie de la confiance selon la taille du conséquent]]. Seules les règles dont l'antécédent est lui-même un [[Support d'un itemset|itemset de support connu]] peuvent être évaluées sans parcours supplémentaire de la base.

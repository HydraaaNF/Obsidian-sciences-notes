#dmv-frequent_itemsets_mining

# Algorithme

Le calcul des [[Règle d'association et confiance|règles d'association]] qui atteignent les seuils fixés se fait en deux étapes.

1. Calculer les [[Itemset fréquent|itemsets fréquents]] : découvrir les itemsets dont le support atteint $minsup$. Cette étape est **très coûteuse** en calcul.
2. Calculer les règles d'association qui tiennent : partitionner chaque itemset fréquent en une prémisse $X$ et un conséquent $Y$, et ne retenir que les règles de confiance $c \ge minconf$. Cette étape est **bien plus rapide** que la découverte des itemsets.

La seconde étape ne crée aucune règle nouvelle sur les items : elle découpe chaque itemset fréquent $F$ déjà obtenu. Pour un itemset de taille $|F| = k$, il y a $2^k - 2$ découpages possibles de $F$ en deux parties non vides, donc autant de règles candidates $X \to Y$ avec $X \cap Y = \varnothing$ et $X \cup Y = F$. Sur les transactions d'un supermarché, cadre de l'[[Analyse du panier de la ménagère]], la première étape dégage les groupes d'articles achetés ensemble et la seconde en tire les règles.

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

**Étape 1.** L'itemset $\{bread, butter, chocolate\}$ est acheté ensemble dans $4/6 = 66\%$ des transactions : il est fréquent pour tout $minsup$ inférieur ou égal à $4$ en support absolu.

**Étape 2.** Les découpages de cet itemset donnent, entre autres :

- $\{butter, chocolate\} \to \{bread\}$ : confiance $4/5 = 80\%$ ;
- $\{chocolate\} \to \{bread, butter\}$ : confiance $4/6 = 66\%$.

Avec $minconf = 70\%$, la première règle tient et la seconde est écartée.

# Interprétation

Le coût du calcul est presque entièrement porté par la première étape, parce que l'information produite par celle-ci suffit à la seconde.

La confiance d'une règle $X \to Y$ tirée de $F$ s'écrit

$$c = \frac{\mathrm{support}(X \cup Y)}{\mathrm{support}(X)} = \frac{\mathrm{support}(F)}{\mathrm{support}(X)}$$

Les deux supports du membre de droite sont connus dès que les itemsets fréquents et leurs supports sont calculés : la seconde étape combine des valeurs déjà obtenues et n'exige plus de compter les occurrences dans la base.

La première étape fixe donc le coût total : elle doit compter le support de chaque itemset candidat, et le nombre de candidats croît très vite avec le nombre d'items et la taille des itemsets recherchés. C'est ce comptage que l'[[Algorithme Apriori]] organise.

# Remarque

Seules les règles de confiance élevée présentent un intérêt ; une règle n'est retenue que si $c \ge minconf$, ce qui écarte la majorité des $2^k - 2$ découpages d'un itemset de taille $k$.

L'ordre des deux étapes est contraint : on ne peut partitionner que des itemsets déjà identifiés, donc la seconde étape ne peut pas précéder la première.

La seconde étape est détaillée par la [[Génération des règles d'association]], qui exploite la structure des itemsets fréquents pour éviter d'énumérer tous les découpages.

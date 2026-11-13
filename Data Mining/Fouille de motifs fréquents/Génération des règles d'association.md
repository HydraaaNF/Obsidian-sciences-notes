#dmv-frequent_itemsets_mining

# Définition

Soit $F$ un [[Itemset fréquent|itemset fréquent]] de taille $k$. Une règle d'association issue de $F$ s'écrit $X \to Y$ avec $X \cup Y = F$ et $X \cap Y = \varnothing$, l'antécédent $X$ et le conséquent $Y$ étant tous deux non vides. Une telle [[Règle d'association et confiance|règle]] correspond donc à une **partition** de $F$ en deux blocs non vides, et la génération des règles consiste à énumérer ces partitions puis à ne retenir que celles dont la confiance atteint $minconf$.

# Propriétés

Un itemset de taille $k$ possède $2^k$ parties, mais deux d'entre elles donnent une partition dégénérée : $X = F$, qui correspond à la règle $F \to \varnothing$, et $X = \varnothing$, qui correspond à la règle $\varnothing \to F$. Aucune des deux n'a de sens, d'où le nombre de règles candidates.

$$N(k) = 2^{k} - 2$$

- $k = 2$ : $2$ règles
- $k = 3$ : $6$ règles
- $k = 4$ : $14$ règles
- $k = 5$ : $30$ règles
- $k = 10$ : $1022$ règles

Le nombre de règles explose donc exponentiellement avec la taille de l'itemset, et chaque itemset fréquent porte à lui seul ces $2^k - 2$ règles candidates ; c'est la baisse de $minsup$, et non la taille des itemsets, qui fait croître le nombre d'itemsets fréquents. Toutes les règles d'un même $F$ partagent le même numérateur dans la confiance, $\mathrm{support}(F)$ ; seule varie la valeur $\mathrm{support}(X)$ de leur antécédent, et les antécédents distincts sont eux aussi en nombre exponentiel.

# Algorithme

La génération s'appuie sur les itemsets fréquents déjà extraits. Elle parcourt chaque itemset de taille $k \ge 2$, teste d'abord ses $(k-1)$-sous-ensembles comme antécédents, puis étend récursivement les conséquents retenus.

```text
Entrée : T, minsup, minconf, F_all = union de F_1 ... F_n

H_1 = ∅
pour chaque f_k ∈ F_all, k ≥ 2, faire
    A = (k-1)-itemsets a_{k-1} tels que a_{k-1} ⊂ f_k
    pour chaque a_{k-1} ∈ A, faire
        conf = support(f_k) / support(a_{k-1})
        si conf ≥ minconf, alors
            sortir la règle a_{k-1} → (f_k - a_{k-1})
            ajouter (f_k - a_{k-1}) à H_1
    ap-genrules(f_k, H_1)
```

Le premier niveau énumère les $k$ antécédents de taille $k-1$ et conserve ceux qui passent le seuil de confiance ; $H_1$ rassemble les conséquents d'un seul item ainsi validés. L'étape récursive [[Algorithme ap-genrules|ap-genrules]] fabrique ensuite des conséquents plus grands, selon le même principe que la [[Génération des candidats par apriori-gen|génération des candidats d'Apriori]].

Le pseudo-code initialise $H_1$ une seule fois, avant la boucle sur les itemsets ; à la lecture, cet ensemble se réinitialise à chaque $f_k$ : partagé entre itemsets, il contiendrait dès le deuxième des conséquents qui ne sont pas des sous-ensembles de l'itemset courant, et $\mathrm{support}(f_k - h)$ serait alors calculé sur un ensemble qui n'en est pas un.

# Interprétation

La solution naïve consiste, pour chaque itemset fréquent $F$, à énumérer ses $2^k - 2$ partitions et à calculer la confiance de chacune en lisant les deux supports nécessaires. Le coût est doublement défavorable : le nombre de règles d'un seul itemset est exponentiel en sa taille, et chacune demande le calcul d'une confiance, qui se lit sur les supports déjà calculés des itemsets fréquents. Sur l'ensemble des itemsets fréquents, le travail est donc de l'ordre de la somme des $2^{|F|} - 2$, à comparer au nombre d'itemsets fréquents, bien plus petit.

Énumérer toutes les partitions est ainsi exclu dès que les itemsets fréquents dépassent quelques items. La génération doit élaguer : elle s'appuie pour cela sur l'[[Anti-monotonie de la confiance selon la taille du conséquent|anti-monotonie de la confiance selon la taille du conséquent]], qui garantit qu'une règle de confiance insuffisante n'a aucun prolongement de confiance suffisante.

# Remarque

L'élagage se lit directement dans la récursion. Pour un itemset $F$ fixé, la confiance décroît quand le conséquent grandit : si un conséquent $h$ de taille $m$ donne une confiance inférieure à $minconf$, tout conséquent plus grand qui le contient donne une confiance au plus égale, et la branche est abandonnée sans calcul. C'est la seule propriété d'ordre disponible ici, la confiance n'étant [[Monotonie de la confiance|ni monotone ni anti-monotone]] entre règles quelconques.

Cette génération est la seconde étape du [[Calcul des règles d'association en deux étapes|calcul en deux étapes]], la plus rapide des deux : les itemsets fréquents fournis par [[Algorithme Apriori|Apriori]] limitent les numérateurs possibles, et seules les partitions réellement candidates sont testées.

#adm-4 #adm-9

# Définition

Une **règle de décision** associe à toute observation $x$ une classe $y$ parmi $K$ classes possibles :

$$D : x \in X \to y = D(x) \in \{1, \dots, K\}$$

Pour une fonction de coût $l_{jk}$ (le coût de décider la classe $j$ alors qu'il s'agit en fait de la classe $k$), le risque conditionnel de décider la classe $j$ après avoir observé $x$ est

$$R(D(x) = j \mid x) = \sum_{k=1}^{K} l_{jk} \mathbb{P}[\text{classe}(x) = k]$$

et conduit au risque théorique (moyen)

$$\mathbb{E}[R(D(x))] = \int_X R(D(x) \mid x) p(x)\,dx$$

# Propriétés

La **règle de décision de Bayes** (aussi appelée règle du maximum a posteriori (MAP)) choisit pour une observation $x$ la classe $i$ telle que

$$R(D(x) = i \mid x) < R(D(x) = j \mid x) \quad \forall j \neq i$$

Elle minimise le risque moyen $\mathbb{E}[R(D(x))]$.

Dans le cadre de plusieurs hypothèses concurrentes $H_i$ et d'une observation $X$, chaque hypothèse porte une probabilité a priori $\mathbb{P}(H_i)$ et une vraisemblance $\mathbb{P}(X \mid H_i)$, que la formule de Bayes combine en probabilité a posteriori :

$$\mathbb{P}(H_i \mid X) = \frac{\mathbb{P}(X \mid H_i)\mathbb{P}(H_i)}{\mathbb{P}(X)}.$$

Le dénominateur $\mathbb{P}(X) = \sum_j \mathbb{P}(X \mid H_j)\mathbb{P}(H_j)$ ne dépend pas de l'hypothèse : il normalise les probabilités a posteriori sans changer leur classement, ce qui permet de le laisser de côté dans la comparaison. La règle du maximum a posteriori retient ainsi l'hypothèse

$$H^\star = \arg\max_i \mathbb{P}(H_i \mid X) = \arg\max_i \mathbb{P}(X \mid H_i)\mathbb{P}(H_i).$$

Le **test bayésien de coût minimum** généralise cette règle : à chaque couple d'hypothèses est associé un coût $C_{i\mid j}$, coût de la décision $H_i$ lorsque l'hypothèse vraie est $H_j$, et l'on retient la décision de plus faible risque a posteriori,

$$\sum_j C_{i\mid j}\mathbb{P}(H_j \mid X) = \frac{1}{\mathbb{P}(X)}\sum_j C_{i\mid j}\mathbb{P}(X \mid H_j)\mathbb{P}(H_j),$$

soit, le facteur $1/\mathbb{P}(X)$ étant commun à toutes les décisions,

$$H^\star = \arg\min_i \sum_j C_{i\mid j}\mathbb{P}(X \mid H_j)\mathbb{P}(H_j).$$

Le risque a posteriori d'une décision $H_i$ additionne les contributions de toutes les hypothèses, chacune pondérée par le coût de décider $H_i$ alors que $H_j$ est vraie. L'écriture réduite au seul terme diagonal $\mathbb{P}(X \mid H_i)\mathbb{P}(H_i)C_{i\mid i}$ est une erreur fréquente : pour un coût 0-1, $C_{i\mid i} = 0$ annule ce terme pour toutes les hypothèses et la comparaison ne départage plus rien. Pour un coût 0-1, le risque a posteriori de décider $H_i$ vaut $\sum_{j \neq i}\mathbb{P}(X \mid H_j)\mathbb{P}(H_j) = \mathbb{P}(X) - \mathbb{P}(X \mid H_i)\mathbb{P}(H_i)$ : le minimiser revient à maximiser $\mathbb{P}(X \mid H_i)\mathbb{P}(H_i)$, et le test de coût minimum se réduit à la règle du maximum a posteriori.

La règle exige la connaissance des probabilités a priori $\mathbb{P}(H_i)$ ; sans elles, la seule comparaison des vraisemblances ne définit pas de décision bayésienne. La maximisation de la probabilité a posteriori est l'opération qui définit l'[[Estimateur du maximum a posteriori|estimateur du maximum a posteriori]], appliquée ici à une hypothèse plutôt qu'à un paramètre ; elle s'oppose au [[Test du rapport de vraisemblance|test du rapport de vraisemblance]], qui compare les seules vraisemblances par le [[Lemme de Neyman-Pearson]]. Le risque a posteriori minimisé par le test de coût minimum est par ailleurs l'analogue, pour une décision, du [[Risque et risque empirique|risque espéré]] minimisé par une fonction de prédiction.

# Exemple

On souhaite classer un pixel en classe 1 (sombre) et classe 2 (clair).

- Si l'on ne sait rien du pixel, on décide selon $\max_k \mathbb{P}[C_k]$ : la classe la plus probable a priori l'emporte : ici, c'est sombre.
- Si l'on connaît la valeur du pixel, on utilise les densités conditionnelles $p(x \mid C_k)$ et l'on choisit selon les probabilités a posteriori $\mathbb{P}[C_k \mid x]$.

L'image considérée comporte une région sombre et une région claire, chacune bruitée ; chaque pixel doit être affecté à l'une des deux classes. Les densités conditionnelles de la luminance selon la classe se recouvrent partiellement :

```chart
type: line
labels: ["0", "25", "50", "75", "100", "125", "150", "175", "200", "225", "250"]
series:
  - title: "p(x|C1)"
    data: [0.0023, 0.0053, 0.0088, 0.0099, 0.0075, 0.0039, 0.0013, 0.0003, 0.0001, 0, 0]
  - title: "p(x|C2)"
    data: [0.0001, 0.0001, 0.0001, 0.0006, 0.0033, 0.0094, 0.0133, 0.0094, 0.0033, 0.0006, 0.0001]
  - title: "p(x)"
    data: [0.0017, 0.004, 0.0066, 0.0076, 0.0065, 0.0053, 0.0043, 0.0026, 0.0009, 0.0002, 0]
```

Valeurs relevées sur la figure, approximatives. La classe 1 (sombre) est centrée sur les faibles luminances et la classe 2 (clair) sur les fortes luminances ; la densité $p(x)$ de la luminance est le mélange des deux.

Les probabilités a posteriori évoluent en sens inverse le long de la luminance : une luminance faible conduit à décider la classe sombre, une luminance élevée à décider la classe claire, et au point où les deux courbes se croisent, les deux décisions sont équivalentes.

```chart
type: line
labels: ["0", "25", "50", "75", "100", "125", "150", "175", "200", "225", "250"]
series:
  - title: "p(C1|x)"
    data: [0.998, 0.998, 0.996, 0.981, 0.873, 0.554, 0.232, 0.092, 0.044, 0.028, 0.023]
  - title: "p(C2|x)"
    data: [0.002, 0.002, 0.004, 0.019, 0.127, 0.446, 0.768, 0.908, 0.956, 0.972, 0.977]
```

Valeurs relevées sur la figure, approximatives.

# Remarque

D'autres règles de décision sont présentées dans [[Règles de décision optimales]] ; en classification, la décision bayésienne est reprise par le [[Classifieur naïf de Bayes]] et par l'[[Analyse discriminante linéaire]].

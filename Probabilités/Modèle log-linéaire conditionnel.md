#adm-8

# Modèle

Un modèle log-linéaire conditionnel décrit la loi conditionnelle d'une étiquette $Y$ sachant une observation $X = x$, sans modéliser la loi de $X$. Il est déterminé par :

- un ensemble $\mathcal{Y}$ d'étiquettes possibles ;
- un jeu de $m$ fonctions de traits $f_1, \dots, f_m$, chacune associant à un couple $(x, y)$ un nombre réel, le plus souvent un indicateur binaire valant $0$ ou $1$ (voir [[Fonctions de traits d'un exemple de traduction]]) ;
- un vecteur de paramètres $\Lambda = \{\lambda_1, \dots, \lambda_m\}$, un poids par fonction de trait.

La probabilité conditionnelle de l'étiquette $y$ sachant l'observation $x$ vaut alors

$$\mathbb{P}[Y = y \mid X = x; \Lambda] = \frac{1}{Z(x; \Lambda)} \exp\left( \sum_{j=1}^{m} \lambda_j f_j(x, y) \right)$$

où la fonction de partition conditionnelle ne dépend que de l'observation et des paramètres :

$$Z(x; \Lambda) = \sum_{y' \in \mathcal{Y}} \exp\left( \sum_{j=1}^{m} \lambda_j f_j(x, y') \right).$$

La classification associée retient l'étiquette la plus probable conditionnellement à l'observation :

$$\hat{y} = \arg\max_{y \in \mathcal{Y}} \mathbb{P}[Y = y \mid X = x; \Lambda] = \arg\max_{y \in \mathcal{Y}} \sum_{j=1}^{m} \lambda_j f_j(x, y).$$

# Interprétation

À chaque étiquette $y$ le modèle associe le score

$$s_x(y) = \sum_{j=1}^{m} \lambda_j f_j(x, y),$$

combinaison linéaire des valeurs prises par les fonctions de traits sur le couple $(x, y)$. L'exponentielle transforme ce score en un poids strictement positif, puis la division par $Z(x; \Lambda)$ renormalise l'ensemble des poids en une distribution sur $\mathcal{Y}$.

Le rôle de chaque poids se lit directement sur le score :

- un coefficient $\lambda_j$ positif favorise les étiquettes pour lesquelles $f_j(x, y)$ est grand ;
- un coefficient $\lambda_j$ négatif les défavorise ;
- un coefficient nul annule l'influence du trait correspondant ;
- un trait qui ne dépend pas de $y$ prend la même valeur pour toutes les étiquettes et ne modifie donc aucune probabilité relative.

Comme la loi de $X$ n'intervient nulle part, le modèle est purement discriminant : il ne décrit que le passage de l'observation à l'étiquette. Les traits peuvent dépendre simultanément de $x$ et de $y$, ce qui permet d'encoder des configurations précises, par exemple la cooccurrence d'un mot du contexte et d'une classe donnée.

# Propriétés

La distribution est normalisée : la somme des probabilités sur les étiquettes vaut un.

$$\sum_{y \in \mathcal{Y}} \mathbb{P}[Y = y \mid X = x; \Lambda] = \frac{1}{Z(x; \Lambda)} \sum_{y \in \mathcal{Y}} \exp\left( \sum_{j=1}^{m} \lambda_j f_j(x, y) \right) = 1$$

Le vecteur des probabilités conditionnelles est la transformée softmax du vecteur des scores : chaque probabilité est l'exponentielle du score correspondant divisée par la somme des exponentielles de tous les scores.

Comme $Z(x; \Lambda)$ ne dépend pas de $y$, il est inutile de le calculer pour classer : comparer les probabilités revient à comparer les scores.

### Démonstration

La fonction de partition est par construction égale au dénominateur commun des probabilités, donc

$$\sum_{y \in \mathcal{Y}} \frac{1}{Z(x; \Lambda)} \exp\left( \sum_{j=1}^{m} \lambda_j f_j(x, y) \right) = \frac{Z(x; \Lambda)}{Z(x; \Lambda)} = 1 .$$

Pour l'argmax, la division par une quantité strictement positive et indépendante de $y$ ne change pas l'ordre des probabilités, et l'exponentielle est strictement croissante : l'étiquette qui maximise $\mathbb{P}[Y = y \mid X = x; \Lambda]$ est celle qui maximise $\sum_{j=1}^{m} \lambda_j f_j(x, y)$.

L'ajout d'une même constante $c$ à tous les scores ne modifie pas la distribution, puisque le facteur $\exp(c)$ apparaît au numérateur comme au dénominateur et s'y simplifie. Seules les différences entre scores déterminent les probabilités.

# Algorithme

Pour classer une observation $x$ :

```
pour chaque étiquette y de l'ensemble des étiquettes :
    s(y) <- somme des lambda_j * f_j(x, y) pour j = 1, ..., m
retourner l'étiquette y dont le score s(y) est maximal
```

Aucune évaluation de la fonction de partition n'est nécessaire, ce qui rend la classification peu coûteuse dès lors que le nombre d'étiquettes reste modeste.

# Exemple

Dans un exemple de traduction, les traits sont des indicateurs binaires. Le trait

$$f_i(x, y) = \mathbb{1}[\text{« April » suit « in » et } y = \text{« en »}]$$

repère la configuration où le mot observé après *in* est *April* et où la traduction retenue est *en*. Il vaut $1$ exactement pour ce couple, et $0$ pour toutes les autres observations ou traductions.

Le poids $\lambda_i$ mesure alors l'avantage de score accordé à la traduction *en* dans ce contexte précis : si $\lambda_i$ est positif, la probabilité conditionnelle de *en* augmente par rapport aux autres traductions lorsque *April* suit *in*. La [[Espérance empirique d'une fonction de trait|espérance empirique]] d'un tel trait compte la proportion des configurations observées dans les données d'entraînement, et c'est cette proportion que le modèle cherche à reproduire.

# Remarque

Le modèle log-linéaire conditionnel généralise la [[Régression logistique binaire]] à un jeu de traits quelconque. Pour deux étiquettes $\{0, 1\}$, en prenant le trait $f_0(x, y) = \mathbb{1}[y = 1]$, qui joue le rôle d'ordonnée à l'origine de la classe $1$, et les traits $f_j(x, y) = x_j \, \mathbb{1}[y = 1]$ pour $j = 1, \dots, n$, le score vaut $\lambda_0 + \lambda_1 x_1 + \dots + \lambda_n x_n$ pour l'étiquette $1$ et $0$ pour l'étiquette $0$. La formule du modèle se réduit à

$$\mathbb{P}[Y = 1 \mid X = x] = \frac{1}{1 + \exp\left( -\lambda_0 - \lambda_1 x_1 - \dots - \lambda_n x_n \right)},$$

et le log-rapport des probabilités a posteriori s'écrit

$$\ln \frac{\mathbb{P}[Y = 1 \mid X = x]}{\mathbb{P}[Y = 0 \mid X = x]} = \lambda_0 + \lambda_1 x_1 + \dots + \lambda_n x_n,$$

c'est-à-dire un log-rapport linéaire en les $x_j$. La [[Régression logistique multinomiale]] en est le cas à $K$ classes, avec un jeu de coefficients par classe et une normalisation sur les $K$ scores.

Le même cadre s'étend aux séquences : lorsque l'observation et l'étiquette sont des suites et que les traits se décomposent position par position, la fonction de partition est sommée sur toutes les séquences d'étiquettes, ce qui donne le [[Champ aléatoire conditionnel à chaîne linéaire]] et sa [[Décomposition positionnelle des fonctions de traits|décomposition positionnelle des traits]].

Les paramètres $\Lambda$ ne sont pas fixés arbitrairement : ils sont estimés en maximisant la vraisemblance conditionnelle des données, ce qui les relie aux [[Estimation des paramètres par les multiplicateurs de Lagrange|multiplicateurs de Lagrange]] et aux [[Contraintes d'espérance sur les fonctions de traits|contraintes d'espérance]] imposées aux traits.

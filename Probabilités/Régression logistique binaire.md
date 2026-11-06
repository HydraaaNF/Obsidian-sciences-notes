# Modèle

La **régression logistique binaire** décrit la loi conditionnelle d'une classe binaire $Y \in \{0,1\}$ sachant un jeu de variables observées $X = (X_1, \dots, X_n)$. La classe suit une [[Loi de Bernoulli|loi de Bernoulli]], c'est-à-dire une [[Loi binomiale]] à une seule épreuve.

Le modèle pose que le logarithme du rapport des probabilités a posteriori est une combinaison linéaire des $x_i$ :

$$\ln \frac{\mathbb{P}[Y = 1 \mid X]}{1 - \mathbb{P}[Y = 1 \mid X]} = \lambda_0 + \lambda_1 x_1 + \dots + \lambda_n x_n .$$

La probabilité a posteriori de la classe $1$ s'en déduit par inversion :

$$\mathbb{P}[Y = 1 \mid X = x] = \frac{\exp(\lambda_0 + \lambda_1 x_1 + \dots + \lambda_n x_n)}{1 + \exp(\lambda_0 + \lambda_1 x_1 + \dots + \lambda_n x_n)} .$$

Sous forme équivalente, en multipliant numérateur et dénominateur par l'exponentielle opposée,

$$\mathbb{P}[Y = 1 \mid X = x] = \frac{1}{1 + \exp(-\lambda_0 - \lambda_1 x_1 - \dots - \lambda_n x_n)} .$$

# Interprétation

Les réels $\lambda_0, \dots, \lambda_n$ sont les coefficients du modèle : $\lambda_0$ est l'ordonnée à l'origine, $\lambda_i$ le poids de la variable $X_i$.

Le membre de gauche $\ln \frac{p}{1-p}$ est le logarithme du rapport des chances (log-odds) en faveur de la classe $1$. Il croît avec la probabilité de cette classe, vaut $0$ lorsque les deux classes sont équiprobables, et change de signe selon que la classe $1$ est plus ou moins probable que la classe $0$. L'hypothèse du modèle est donc que ce log-rapport est affine en $x$.

Le signe des coefficients résume l'effet des variables :

- $\lambda_i > 0$ : augmenter $x_i$ d'une unité augmente le log-rapport de $\lambda_i$ et favorise la classe $1$ ;
- $\lambda_i < 0$ : augmenter $x_i$ défavorise la classe $1$ ;
- pour $x = 0$, le log-rapport vaut $\lambda_0$.

La probabilité a posteriori est une fonction logistique, ou sigmoïde, du score linéaire $s(x) = \lambda_0 + \lambda_1 x_1 + \dots + \lambda_n x_n$ : elle croît en S de $0$ à $1$, vaut $1/2$ exactement lorsque le score est nul, et tend vers $1$ pour les grands scores positifs et vers $0$ pour les grands scores négatifs. Un score nul signifie que les deux classes sont aussi probables l'une que l'autre.

La transformation du score en probabilité est croissante, donc décider de la classe la plus probable par [[Classification par maximum a posteriori|maximum a posteriori]] revient à comparer le score à $0$ : la frontière entre les deux classes est l'hyperplan $s(x) = 0$.

L'hypothèse de linéarité porte sur le log-rapport des chances, et non sur la probabilité elle-même : c'est ce qui maintient la probabilité dans l'intervalle $[0,1]$ tout en gardant une frontière de décision linéaire.

# Propriétés

Les deux probabilités a posteriori se complètent, puisque $Y$ ne prend que deux valeurs :

$$\mathbb{P}[Y = 0 \mid X = x] = \frac{1}{1 + \exp(\lambda_0 + \lambda_1 x_1 + \dots + \lambda_n x_n)} .$$

Le rapport des chances croît exponentiellement avec le score :

$$\frac{\mathbb{P}[Y = 1 \mid X = x]}{\mathbb{P}[Y = 0 \mid X = x]} = \exp(\lambda_0 + \lambda_1 x_1 + \dots + \lambda_n x_n) .$$

Les deux classes sont prédites avec la même probabilité $1/2$ sur l'hyperplan d'équation

$$\lambda_0 + \lambda_1 x_1 + \dots + \lambda_n x_n = 0 .$$

# Exemple

Pour une seule variable, avec $\lambda_0 = 0$ et $\lambda_1 = 1$, la probabilité a posteriori de la classe $1$ vaut $1/(1+e^{-x})$. Le graphique donne cette probabilité en fonction du score linéaire.

```chart
type: line
labels: ["-6", "-5", "-4", "-3", "-2", "-1", "0", "1", "2", "3", "4", "5", "6"]
series:
  - title: "Probabilité a posteriori de la classe 1"
    data: [0.002, 0.007, 0.018, 0.047, 0.119, 0.269, 0.5, 0.731, 0.881, 0.953, 0.982, 0.993, 0.998]
```

Le point d'inflexion est à l'origine, où la probabilité vaut $1/2$, et la courbe s'aplatit aux deux extrémités sans jamais atteindre $0$ ni $1$. Une variation du score autour de $0$ modifie donc fortement la probabilité, alors qu'elle la modifie très peu loin de $0$.

# Remarque

La régression logistique binaire est le cas à deux classes de la [[Régression logistique multinomiale|régression logistique multinomiale]], qui associe un jeu de coefficients à chaque classe et normalise les scores par un softmax sur l'ensemble des classes.

Elle est aussi un cas particulier du [[Modèle log-linéaire conditionnel]]. Avec une étiquette $y \in \{0,1\}$ et les $n+1$ fonctions de traits

- $f_0(x,y) = \mathbb{1}[y = 1]$ ;
- $f_j(x,y) = x_j \, \mathbb{1}[y = 1]$ pour $j = 1, \dots, n$,

la forme normalisée

$$\mathbb{P}[Y = y \mid X = x] = \frac{1}{Z(x)} \exp\left( \sum_{j=0}^{n} \lambda_j f_j(x,y) \right)$$

attribue le score $s(x) = \lambda_0 + \lambda_1 x_1 + \dots + \lambda_n x_n$ à la classe $1$ et le score $0$ à la classe $0$, d'où $Z(x) = 1 + \exp(s(x))$ : elle se réduit à la probabilité ci-dessus, et la sigmoïde est la version à deux étiquettes du modèle log-linéaire conditionnel.

Le modèle ne spécifie que la loi conditionnelle de $Y$ sachant $X$ ; il ne dit rien de la loi des variables observées $X_1, \dots, X_n$, qui n'ont donc pas à être modélisées.

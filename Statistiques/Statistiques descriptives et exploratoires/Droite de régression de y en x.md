# Théorème

La *droite de régression linéaire* de $y$ en $x$, ou encore *droite des moindres carrés*, cas linéaire de la [[Courbe de régression]], est la droite qui minimise la somme des carrés des erreurs

$$D(a, b) = \frac{1}{n} \sum_{i=1}^n |y_i - a x_i - b|^2 .$$

Elle passe par le point de coordonnées $(\bar{x}, \bar{y})$ et a pour équation

$$y = ax + b$$

où

$$a = \frac{C_{x,y}}{\mathbb{V}(x)}$$

$$b = \bar{y} - a\bar{x}.$$

Dans ces formules, $C_{x,y}$ est la [[Covariance et coefficient de corrélation linéaire|covariance empirique]] entre $x$ et $y$ et $\mathbb{V}(x)$ la [[Variance et écart-type|variance]] des observations de $x$ :

$$C_{x,y} = \frac{1}{n} \sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y}) = \left( \frac{1}{n} \sum_{i=1}^n x_i y_i \right) - \bar{x}\bar{y}$$

$$\mathbb{V}(x) = \frac{1}{n} \sum_{i=1}^n (x_i - \bar{x})^2,$$

où $\bar{x}$ et $\bar{y}$ sont les [[Moyenne, médiane et mode|moyennes arithmétiques]] des observations de $x$ et de $y$.

### Démonstration

On cherche les valeurs $a$ et $b$ qui minimisent la quantité $D(a, b)$ rappelée ci-dessus. Soit $a$ fixé, on cherche le minimum de la fonction $b \to D(a, b)$. On a

$$\begin{aligned} \frac{\partial D(a,b)}{\partial b} &= -\frac{2}{n}\sum_{i=1}^{n}(y_i-ax_i-b) \\ &= -2(\bar{y}-a\bar{x}-b) \end{aligned}$$

ce qui implique que la fonction $b \to D(a, b)$ est minimale au point

$$b = \bar{y} - a\bar{x}.$$

Cherchons à présent à minimiser la fonction

$$f : a \to D(a, \bar{y} - a\bar{x}) = \frac{1}{n} \sum_{i=1}^n (y_i - \bar{y} - a(x_i - \bar{x}))^2 .$$

On a

$$\begin{aligned} f'(a) &= -\frac{2}{n} \sum_{i=1}^n (x_i - \bar{x}) (y_i - \bar{y} - a(x_i - \bar{x})) \\ &= -2C_{x,y} + 2a\mathbb{V}(x). \end{aligned}$$

Si $\mathbb{V}(x)$ est nulle, cela signifie que toutes les observations $x_1, \dots, x_n$ ont la même valeur : le nuage de points forme alors une droite verticale d'équation $x = \bar{x}$. Si $\mathbb{V}(x)$ est non nulle, alors le minimum de la fonction $f$ est atteint pour

$$a = \frac{C_{x,y}}{\mathbb{V}(x)}.$$

En admettant l'existence d'un couple $(a, b)$ qui minimise $D(a, b)$, on doit effectivement chercher ce couple parmi ceux qui annulent les dérivées partielles $\frac{\partial D}{\partial a}$ et $\frac{\partial D}{\partial b}$ ; on constate ici que l'on dispose d'un seul bon candidat.

Finalement, la droite de régression de $y$ en $x$ a pour équation

$$y = \bar{y} + \frac{C_{x,y}}{\mathbb{V}(x)}(x - \bar{x}).$$

# Exemple

Une enquête auprès de 20 foyers a permis de recueillir les informations suivantes : $x_i$ correspond au nombre d'enfants du $i$-ème foyer et $y_i$ à la superficie du logement (en $m^2$). Les observations sont

| $x_i$ | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 2 |
|---|---|---|---|---|---|---|---|---|---|---|
| $y_i$ | 36 | 40 | 34 | 42 | 40 | 53 | 58 | 45 | 43 | 43 |
| $x_i$ | 2 | 2 | 2 | 2 | 2 | 3 | 3 | 3 | 4 | 6 |
| $y_i$ | 48 | 58 | 61 | 46 | 45 | 58 | 66 | 75 | 68 | 90 |

Les différents indicateurs sont

$$\bar{x} = 1.9, \quad \mathbb{V}(x) = 1.89, \quad \bar{y} = 52.45, \quad \mathbb{V}(y) = 194.54, \quad C_{x,y} = 16.645.$$

La forme du [[Nuage de points|nuage de points]] laisse supposer une liaison linéaire, tendance que confirme le coefficient de corrélation linéaire $r(x, y) \approx 0.87$. Le calcul des coefficients $a$ et $b$ donne

$$a = \frac{16.645}{1.89} \approx 8.81$$

$$b = 52.45 - 8.81 \times 1.9 \approx 35.72,$$

d'où l'équation de la droite de régression de $y$ en $x$ :

$$y \approx 8.81x + 35.72.$$

# Interprétation

À l'aide de la droite de régression, on peut effectuer une prédiction de $y$ pour une valeur de $x$ donnée. Par exemple, pour 5 enfants, la superficie de l'appartement attendue est de

$$y \approx 8.81 \times 5 + 35.72 \approx 79.75\,m^{2}.$$

# Remarque

Pour prédire une valeur de $x$ à partir d'une valeur donnée de $y$, il est préférable de calculer la droite de régression de $x$ en $y$ et de se servir de celle-ci, plutôt que d'utiliser la droite de régression de $y$ en $x$.

La variance des observations de $x$ se déduit de la table : $\sum_{i=1}^{20} x_i^2 = 110$, d'où $\mathbb{V}(x) = \frac{110}{20} - 1.9^2 = 1.89$. L'écriture $\mathbb{V}(x) = 1.52$ est une erreur fréquente : elle exigerait $\sum_{i=1}^{20} x_i^2 = 20 \times (1.52 + 1.9^2) = 102.6$, incompatible avec la table. Les coefficients de la droite de régression et le coefficient de corrélation linéaire en découlent : $a \approx 8.81$, $b \approx 35.72$ et $r \approx 0.87$.

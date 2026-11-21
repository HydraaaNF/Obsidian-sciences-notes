#dmv-xai #ml-1

# Modèle

On veut modéliser la probabilité conditionnelle de l'étiquette $Y = 1$ sachant les variables observées $X$. Les deux classes sont complémentaires,

$$\mathbb{P}(Y = 1 \mid X) + \mathbb{P}(Y = 0 \mid X) = 1,$$

donc modéliser $\mathbb{P}(Y = 1 \mid X)$ suffit.

Une probabilité prend ses valeurs dans $[0, 1]$, ce qu'une fonction linéaire ne fait pas. Le [[Modèle linéaire]] est donc conservé comme score, et seule sa sortie est transformée. Le score est la combinaison linéaire

$$y'_i = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \ldots + \beta_n x_n,$$

et la probabilité prédite est l'image de ce score par la fonction sigmoïde

$$y_i = \mathrm{sigmoid}(y'_i) = \frac{1}{1 + e^{-y'_i}}.$$

L'application inverse fait apparaître le log-rapport de chances, ou logit, qui est linéaire dans les variables :

$$\ln \frac{\mathbb{P}(Y = 1 \mid X)}{\mathbb{P}(Y = 0 \mid X)} = \beta_0 + \beta_1 x_1 + \ldots + \beta_n x_n.$$

# Propriétés

La sigmoïde, notée $\sigma$, est caractérisée par les propriétés suivantes.

- Elle envoie $\mathbb{R}$ sur $(0, 1)$.
- En $0$ elle vaut un demi : $\sigma(0) = 0.5$.
- Elle est symétrique : $\sigma(-z) = 1 - \sigma(z)$.
- Sa dérivée s'exprime avec ses propres valeurs : $\sigma'(z) = \sigma(z) \left( 1 - \sigma(z) \right)$.

# Interprétation

Le [[Seuil de décision]] est $0.5$ : on prédit la classe $1$ dès que $\sigma(y'_i) \geq 0.5$, c'est-à-dire dès que le score est positif. Pour deux variables, l'équation

$$\beta_0 + \beta_1 x_1 + \beta_2 x_2 = 0$$

est celle d'une droite : la frontière est linéaire, et le modèle reste un classifieur linéaire malgré la courbure de la sigmoïde.

La valeur absolue du score mesure la confiance de la prédiction, car elle croît avec la distance à cette droite.

- Loin de la droite, la probabilité prédite est proche de $0$ ou de $1$, et le modèle est assuré.
- Sur la droite, la probabilité vaut $0.5$, et le modèle est indécis.

La contribution de chaque variable à la décision est une quantité connue, lue directement dans les coefficients, sans effet noyé dans une structure interne opaque : c'est ce qui fait du modèle logistique un modèle interprétable. Il fournit ainsi un cas typique de modèle [[Interprétabilité|interprétable]].

# Exemple

Probabilité de décès sur le Titanic en fonction de l'âge. La probabilité prédite est

$$y_i = \mathrm{sigmoid}(0.5 + 2 \times Pclass + 0.1 \times Age),$$

et le score correspondant vaut $y'_i = 0.5 + 2 \times Pclass + 0.1 \times Age$. La courbe obtenue est une sigmoïde croissante, faible aux jeunes âges et proche de $1$ aux âges élevés.

- L'axe vertical porte la probabilité de mourir, entre $0.00$ et $1.00$.
- L'axe horizontal porte l'âge, gradué en $25$, $50$ et $75$.
- Les points observés se placent à $0.00$ pour les plus jeunes passagers et à $1.00$ pour les plus âgés.

La règle de décision est binaire : le passager est prédit mort si $y_i \geq 0.5$, vivant sinon, ce qui revient à comparer le score à $0$ sans avoir à calculer la probabilité.

# Remarque

- Un score linéaire transformé par une sigmoïde est exactement l'unité de calcul d'un [[Neurone formel]] : le modèle logistique est un neurone à activation sigmoïde.
- La sigmoïde se lit comme un [[Fonction softmax|softmax]] à deux scores dont l'un est fixé à $0$.
- La dérivée de la sigmoïde revient dans la perte du modèle, voir l'[[Entropie croisée binaire]].
- Le cas à deux classes s'étend à un score par classe dans la [[Régression logistique multinomiale]].

#ml-1

# Modèle

On veut modéliser une probabilité conditionnelle, celle de l'étiquette $Y = 1$ sachant les variables observées $X$. Les deux classes sont complémentaires,

$$\mathbb{P}(Y = 1 \mid X) + \mathbb{P}(Y = 0 \mid X) = 1,$$

donc modéliser $\mathbb{P}(Y = 1 \mid X)$ suffit.

Une probabilité prend ses valeurs dans $[0, 1]$, ce qu'une fonction linéaire ne fait pas. L'astuce consiste à rendre linéaire non pas la probabilité elle-même, mais son log-rapport de chances, appelé logit :

$$\underbrace{\ln \frac{\mathbb{P}(Y = 1 \mid X)}{\mathbb{P}(Y = 0 \mid X)}}_{\text{logit} \in \mathbb{R}} = z = a x_1 + b x_2 + c .$$

L'inversion de cette relation fait apparaître la fonction logistique, ou sigmoïde, qui transforme le score $z$ en probabilité :

$$\mathbb{P}(Y = 1 \mid X) = \sigma(z) = \frac{1}{1 + e^{-z}} .$$

Le modèle est ainsi linéaire à l'intérieur, dans l'expression du logit, et écrasé à l'extérieur, par la sigmoïde qui ramène toute valeur réelle du score dans l'intervalle $(0, 1)$.

# Propriétés

La sigmoïde est caractérisée par les propriétés suivantes.

- Elle envoie $\mathbb{R}$ sur $(0, 1)$.
- $\sigma(0) = 0.5$.
- Elle est symétrique : $\sigma(-z) = 1 - \sigma(z)$.
- Sa dérivée s'exprime avec ses propres valeurs : $\sigma'(z) = \sigma(z) \left( 1 - \sigma(z) \right)$.

# Interprétation

Le [[Seuil de décision]] est $0.5$ : on prédit la classe $1$ dès que $\sigma(z) \geq 0.5$, c'est-à-dire dès que

$$z = a x_1 + b x_2 + c \geq 0 .$$

L'équation

$$a x_1 + b x_2 + c = 0$$

est celle d'une droite. La régression logistique est donc un classifieur linéaire, malgré son nom.

La valeur absolue du score mesure la confiance de la prédiction, car $|z|$ croît avec la distance à cette droite.

- Loin de la droite, la probabilité prédite $\hat{y}$ est proche de $0$ ou de $1$ : le modèle est assuré.
- Sur la droite, $\hat{y} = 0.5$ : le modèle est indécis.

# Remarque

- La [[Régression logistique binaire]] donne la formulation probabiliste du modèle pour un jeu de variables observées $X = (X_1, \dots, X_n)$, avec un coefficient par variable.
- La régression logistique est le cas à deux classes de la [[Régression logistique multinomiale]], qui associe un score à chaque classe et normalise l'ensemble sur les classes.
- La dérivée $\sigma'(z)$ revient dans la perte du modèle, voir l'[[Entropie croisée binaire]].
- Un score linéaire transformé par une sigmoïde est exactement l'unité de calcul d'un [[Neurone artificiel]] : la régression logistique est un neurone à activation sigmoïde.

La sigmoïde se lit aussi comme un [[Fonction softmax|softmax]] à deux scores, dont l'un est fixé à $0$ :

$$\sigma(z) = \frac{1}{1 + e^{-z}} = \frac{e^z}{e^z + 1} = \frac{e^z}{e^z + e^0} .$$

Chaque classe reçoit l'exponentielle de son score, divisée par le total. Fixer le score de l'une des deux classes à $0$ ne coûte rien : seul compte l'écart entre les deux scores, et

$$\ln \frac{\mathbb{P}(\text{chien})}{\mathbb{P}(\text{chat})} = z_{\text{chien}} - z_{\text{chat}}$$

redonne le logit du modèle. Avec deux classes et l'un des deux scores nul, le softmax redonne ainsi la sigmoïde.

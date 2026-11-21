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
- Sa dérivée s'exprime avec ses propres valeurs : $\frac{d\sigma}{dz}(z) = \sigma(z) \left( 1 - \sigma(z) \right)$.

# Algorithme

Entraîner le modèle, c'est chercher les paramètres $(a^*, b^*, c^*)$ qui minimisent l'opposé de la log-vraisemblance sur les données observées :

$$(a^*, b^*, c^*) = \operatorname*{argmin}_{(a,b,c)} \left( -LL(a, b, c) \right)$$

C'est la même [[Descente de gradient]] que pour la [[Régression linéaire]] : seule la perte change.

À chaque pas, le gradient rassemble une dérivée partielle par paramètre,

$$\nabla(-LL)(a_t, b_t, c_t) = \left( \frac{\partial (-LL)}{\partial a}, \frac{\partial (-LL)}{\partial b}, \frac{\partial (-LL)}{\partial c} \right)(a_t, b_t, c_t),$$

et la mise à jour déplace tous les paramètres à la fois :

$$(a_{t+1}, b_{t+1}, c_{t+1}) = (a_t, b_t, c_t) - \alpha \times \nabla(-LL)(a_t, b_t, c_t).$$

Le vecteur complet est calculé par `autograd`, sans dériver chaque composante à la main : voir [[Différenciation automatique]].

# Interprétation

Le [[Seuil de décision]] est $0.5$ : on prédit la classe $1$ dès que $\sigma(z) \geq 0.5$, c'est-à-dire dès que

$$z = a x_1 + b x_2 + c \geq 0 .$$

L'équation

$$a x_1 + b x_2 + c = 0$$

est celle d'une droite. La régression logistique est donc un classifieur linéaire, malgré son nom.

La valeur absolue du score mesure la confiance de la prédiction, car $|z|$ croît avec la distance à cette droite.

- Loin de la droite, la probabilité prédite $\hat{y}$ est proche de $0$ ou de $1$ : le modèle est assuré.
- Sur la droite, $\hat{y} = 0.5$ : le modèle est indécis.

La lecture des coefficients comme effets sur le score, qui fait de ce modèle un modèle blanc, est traitée dans le [[Lien logistique comme modèle interprétable|modèle logistique interprétable]].

# Remarque

- Un score linéaire transformé par une sigmoïde est exactement l'unité de calcul d'un [[Neurone artificiel]] : la régression logistique est un neurone à activation sigmoïde.
- La [[Composition de couches linéaires]] échoue sur le ou exclusif comme la régression logistique, dont la perte y stagne à $\ln 2 = 0.693$.
- Le gradient de l'entropie croisée binaire garde la forme prédiction moins vérité du [[Gradient du couple softmax et entropie croisée]], la sigmoïde jouant le rôle du softmax à deux classes.

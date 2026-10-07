# Définition

La **méthode des moments** consiste à exprimer analytiquement les moments en fonction du paramètre, puis à estimer la valeur du paramètre à partir des estimations empiriques de ces moments.

Soient $g_i$ des fonctions telles que $\forall \theta \in \Theta$, $\mathbb{E}_\theta[g_i(X)] < \infty$. Les choix typiques sont $g_i(x) = x^i$ ou $g_i(x) = I(x \in \Delta_i)$.

Les estimateurs de moments sont les solutions du système d'équations

$$\mathbb{E}_\theta[g_i(x)] = \overline{\mu}_i$$

où les $\overline{\mu}_i$ désignent les estimations empiriques des moments ; ce sont des [[Estimateur|estimateurs]] du paramètre $\theta$.

# Exemple

La durée de vie d'un composant est modélisée par une [[Loi gamma|loi gamma]] de densité

$$f(x; \alpha, \lambda) = [\lambda^\alpha / \Gamma(\alpha)]x^{\alpha-1}\exp(-\lambda x)$$

En considérant les deux moments

$$\mu_1(\theta) = \mathbb{E}_\theta[X] = \alpha/\lambda$$

$$\mu_2(\theta) = \mathbb{E}_\theta[X^2] = \alpha(1+\alpha)/\lambda^2$$

le système d'équations admet une solution unique

$$\alpha = \left(\frac{\mu_1(\theta)}{\sigma(\theta)}\right)^2$$

$$\lambda = \frac{\mu_1(\theta)}{\sigma^2(\theta)}$$

où $\sigma^2(\theta) = \mu_2(\theta) - \mu_1^2(\theta)$.

En remplaçant les moments par leurs estimations empiriques, on obtient les estimateurs de moments.

# Remarque

Le [[Estimateur du maximum de vraisemblance|maximum de vraisemblance]] est une autre méthode d'estimation d'un paramètre.

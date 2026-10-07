# Définition

L'apprentissage consiste à rechercher une bonne fonction dans un espace de fonctions $\mathcal{F}$, appelé **espace d'hypothèses**. C'est le cadre dans lequel se posent les [[Problèmes d'apprentissage statistique|problèmes d'apprentissage statistique]].

# Exemple

Exemples de fonctions paramétriques :

- **Régression** :
  $$\hat{y} = f(x; a, b) = a \cdot x + b$$
- **Classification** :
  $$\hat{y} = f(x; a, b) = \operatorname{sign}(a \cdot x + b)$$
- **Estimation de densité** :
  $$\hat{p}(z) = f(z; \mu, \Sigma) = \frac{1}{(2\pi)^{\frac{d}{2}} \sqrt{|\Sigma|}} \exp\left(-\frac{1}{2}(z - \mu)^T \Sigma^{-1}(z - \mu)\right)$$

# Remarque

- La qualité d'une fonction de $\mathcal{F}$ se mesure par une [[Fonction de perte]] ; c'est sur elle que se construit le [[Risque et risque empirique|risque]].
- Dans la densité gaussienne, l'exposant du facteur de normalisation est la moitié de la dimension $d$ de $z$ : c'est cette valeur qui assure que l'intégrale de la densité sur $\mathbb{R}^d$ vaut $1$. L'écriture $(2\pi)^{|z|/2}$, où l'exposant dépendrait de la valeur de $z$ plutôt que de la dimension, est une erreur fréquente.

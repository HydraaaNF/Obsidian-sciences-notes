# Propriétés

L'[[Algorithme d'espérance-maximisation|algorithme d'espérance-maximisation]] (EM) vérifie les deux propriétés suivantes, où $Q$ désigne la [[Fonction auxiliaire de l'algorithme d'espérance-maximisation|fonction auxiliaire]].

## Propriété 1

La suite des estimateurs $\theta_n$ est telle que la [[Fonction de vraisemblance|vraisemblance]] des données augmente à chaque itération de l'algorithme.

On peut montrer que

$$Q(\theta, \theta_i) - Q(\theta_i, \theta_i) = \ln p(\mathbf{x} \mid \theta) - \ln p(\mathbf{x} \mid \theta_i) + \underbrace{\mathbb{E} \left[ \ln \frac{p(\mathbf{z} \mid \mathbf{x}, \theta)}{p(\mathbf{z} \mid \mathbf{x}, \theta_i)} \mid \mathbf{x}, \theta_i \right]}_{<0}$$

ce qui implique que

$$Q(\theta_{i+1}, \theta_i) \geq Q(\theta_i, \theta_i) \Rightarrow p(\mathbf{x} \mid \theta_{i+1}) \geq p(\mathbf{x} \mid \theta_i)$$

## Propriété 2

L'algorithme EM permet le calcul du gradient de la fonction de log-[[Fonction de vraisemblance|vraisemblance]] aux points $\theta_i$.

On peut vérifier que, sous des hypothèses peu restrictives,

$$\frac{\partial Q(\theta,\theta_i)}{\partial\theta}\Big|_{\theta=\theta_i}=\frac{\partial\ln f(\mathbf{x};\theta)}{\partial\theta}\Big|_{\theta=\theta_i}+\underbrace{\frac{\partial \mathbb{E}[\ln p(\mathbf{z}\mid\mathbf{x};\theta)\mid\mathbf{x};\theta_i]}{\partial\theta}\Big|_{\theta=\theta_i}}_{=0}$$

## Convergence

Les deux propriétés précédentes impliquent que l'estimation EM converge vers les points stationnaires de la fonction de log-vraisemblance $\ln p(\mathbf{x}; \theta)$.

# Remarque

La convergence n'est garantie que vers un maximum local de la fonction de vraisemblance $\ln p(\mathbf{x}; \theta)$ :

- il faut une bonne estimation initiale $\theta_0$ ;
- il faut éviter les solutions dégénérées (voir [[Espérance-maximisation pour un mélange de gaussiennes]]).

En pratique, la convergence est contrôlée par deux facteurs :

- l'augmentation de la log-vraisemblance des données ;
- un nombre fixé d'itérations.

Des contraintes sur l'espace des paramètres sont souvent utilisées pour éviter les mauvaises solutions ou les solutions dégénérées, par exemple :

- un plancher de variance (« minimum variance floor ») ;
- une initialisation fondée sur l'[[k-means|algorithme des k-moyennes]] (segmental).

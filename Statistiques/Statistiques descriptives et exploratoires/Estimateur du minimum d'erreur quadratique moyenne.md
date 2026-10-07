# Définition

L'[[Estimateur|estimateur]] du minimum d'erreur quadratique moyenne (MMSE) minimise l'[[Erreur quadratique moyenne|erreur quadratique moyenne]] ; il est donné par l'[[Espérance conditionnelle|espérance conditionnelle]] de $\theta$ sachant $x$ :

$$\mathbb{E}[\theta \mid x] = \operatorname{argmin} \mathbb{E}[(\hat{\theta} - \theta)^2]$$

# Remarque

L'erreur quadratique moyenne minimisée s'écrit différemment selon le point de vue adopté :

- **point de vue bayésien** (voir [[Estimation bayésienne]]) : $\mathbb{E}_{\theta \mid x}[(\hat{\theta} - \theta)^2]$, avec $\mathcal{L}(\theta \mid x)$ connue ;
- **point de vue fréquentiste** : $\mathbb{E}_{\theta}[(\hat{\theta} - \theta)^2]$, avec $\theta$ inconnu.

Le calcul de l'estimateur nécessite de manipuler $p(x) = \int_{\theta'} p(x \mid \theta')p(\theta')$, puisque $p(\theta \mid x) = \frac{p(x \mid \theta)p(\theta)}{p(x)}$. Ce n'est pas le cas de l'[[Estimateur du maximum a posteriori|estimateur du maximum a posteriori]], car

$$\operatorname{argmax}_{\theta} \frac{p(x \mid \theta)p(\theta)}{p(x)} = \operatorname{argmax}_{\theta} p(x \mid \theta)p(\theta)$$

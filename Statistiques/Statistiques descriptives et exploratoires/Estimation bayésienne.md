# Définition

L'**estimation bayésienne** définit deux estimateurs du paramètre $\theta$.

**Maximum a posteriori (MAP).** L'[[Estimateur du maximum a posteriori|estimateur du maximum a posteriori]] est donné par

$$\hat{\theta} = \operatorname{argmax}_{\theta} p(\theta \mid x) = \operatorname{argmax}_{\theta} p(x \mid \theta)p(\theta)$$

**Minimum d'erreur quadratique moyenne (MMSE).** L'[[Estimateur du minimum d'erreur quadratique moyenne|estimateur du minimum d'erreur quadratique moyenne]] est donné par

$$\hat{\theta} = \mathbb{E}[\theta \mid x] = \int \theta p(\theta \mid x)\, d\theta = \frac{\int \theta p(x \mid \theta)p(\theta)\, d\theta}{p(x)}$$

# Propriétés

Les estimateurs bayésiens sont asymptotiquement équivalents à l'[[Estimateur du maximum de vraisemblance|estimateur du maximum de vraisemblance]].

# Interprétation

L'estimation bayésienne présente plusieurs atouts :

- elle couvre le cas des petits échantillons ;
- elle traite finement l'incertitude, via $\mathcal{L}(\theta \mid x)$ ;
- elle adopte le point de vue bayésien : $\theta \sim \mathcal{L}(\theta)$ ;
- elle permet d'intégrer une connaissance experte ou un a priori.

# Remarque

La forme correcte de l'espérance a posteriori est
$$\mathbb{E}[\theta \mid x] = \frac{\int \theta p(x \mid \theta)p(\theta)\, d\theta}{p(x)}$$

$$p(x) = \int p(x \mid \theta)p(\theta)\, d\theta.$$
L'écriture sans le facteur de normalisation $p(x)$, c'est-à-dire $\int \theta p(x \mid \theta)p(\theta)\, d\theta$, est une erreur fréquente : cette intégrale vaut $p(x)\,\mathbb{E}[\theta \mid x]$ et non $\mathbb{E}[\theta \mid x]$.

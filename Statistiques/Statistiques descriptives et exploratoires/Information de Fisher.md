# Définition

On appelle **quantité d'information de Fisher** sur le paramètre $\theta$ apportée par un échantillon de taille $n$ la quantité positive (ou nulle) suivante :

$$I_n(\theta) = \mathbb{E}\left[ \left( \frac{\partial}{\partial \theta} \mathcal{L}\mathcal{L}(X_1, \dots, X_n; \theta) \right)^2 \right] \quad \text{si elle existe.}$$

où $\mathcal{L}\mathcal{L}(X_1, \dots, X_n; \theta)$ est la [[Fonction de vraisemblance|log-vraisemblance]] de l'[[Échantillon et échantillonnage|échantillon]], utilisée pour construire l'[[Estimateur du maximum de vraisemblance]]. On note $I_1(\theta)$ l'information apportée par une seule observation.

# Interprétation

La quantité $I_n(\theta)$ mesure la quantité d'information qu'un échantillon de taille $n$ apporte sur le paramètre $\theta$ : plus elle est grande, plus l'échantillon est informatif sur ce paramètre.

# Propriétés

Sous l'hypothèse de Cramér-Rao (le domaine de définition de $X$ ne dépend pas du paramètre $\theta$), le calcul de l'information se simplifie (voir [[Calcul de l'information de Fisher sous hypothèse de Cramér-Rao]]) :

$$I_n(\theta) = -\mathbb{E}\left[ \frac{\partial^2}{\partial \theta^2} \mathcal{L}\mathcal{L}(X_1, \dots, X_n; \theta) \right] \quad \text{si elle existe.}$$

**Additivité de l'information.** Sous la même hypothèse,

$$I_n(\theta) = nI_1(\theta).$$

Cela signifie que chaque observation a la même importance et plus on dispose d'observations, plus l'information augmente.

### Démonstration

Sous l'hypothèse de Cramér-Rao, on peut utiliser la forme simplifiée de l'information. Soit $n \in \mathbb{N}^*$, les variables $X_1, \dots, X_n$ étant i.i.d., on a

$$\begin{aligned} I_n(\theta) &= -\mathbb{E}\left[ \frac{\partial^2}{\partial \theta^2} \mathcal{L}\mathcal{L}(X_1, \dots, X_n; \theta) \right] \\ &= -\mathbb{E}\left[ \frac{\partial^2}{\partial \theta^2} \ln \mathcal{L}(X_1, \dots, X_n; \theta) \right] \\ &= -\mathbb{E}\left[ \frac{\partial^2 \ln(\mathcal{L}(X_1; \theta) \times \cdots \times \mathcal{L}(X_n; \theta))}{\partial \theta^2} \right] \\ &= -\mathbb{E}\left[ \sum_{i=1}^n \frac{\partial^2 \ln \mathcal{L}(X_i; \theta)}{\partial \theta^2} \right] \\ &= -n\mathbb{E}\left[ \frac{\partial^2 \ln \mathcal{L}(X_1; \theta)}{\partial \theta^2} \right] \\ &= nI_1(\theta). \end{aligned}$$

# Exemple

**Information sur la moyenne d'une loi normale.** On considère un échantillon $(X_1, \dots, X_n)$ de variable mère $X$ suivant une [[Loi gaussienne|loi normale]] $\mathcal{N}(\mu, \sigma^2)$ avec $\mu$ inconnu et $\sigma^2$ connu. L'ensemble des valeurs prises par $X$ est $\mathbb{R}$ tout entier, il ne dépend donc pas de $\mu$ ; l'hypothèse de Cramér-Rao est ainsi satisfaite et l'on a

$$\begin{aligned} I_1(\mu) &= -\mathbb{E}\left[ \frac{\partial^2 \ln \mathcal{L}(X_1; \mu)}{\partial \mu^2} \right] \\ &= -\mathbb{E}\left[ \frac{\partial^2}{\partial \mu^2} \ln\left( \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(X_1-\mu)^2}{2\sigma^2}} \right) \right] \\ &= -\mathbb{E}\left[ \frac{\partial^2}{\partial \mu^2} \left( -\ln\left( \sqrt{2\pi\sigma^2} \right) - \frac{(X_1-\mu)^2}{2\sigma^2} \right) \right] \\ &= \mathbb{E}\left[ \frac{1}{\sigma^2} \right] \\ &= \frac{1}{\sigma^2}. \end{aligned}$$

Ainsi, l'information apportée par une observation sur la moyenne $\mu$ est d'autant plus grande que la variance est petite.

**Information sur le paramètre d'une loi de Poisson.** On considère un échantillon de variable mère $X$ suivant une [[Loi de Poisson|loi de Poisson]] de paramètre $\lambda$ inconnu. L'ensemble des valeurs prises par $X$ est $\mathbb{N}$, qui ne dépend pas de $\lambda$ ; l'hypothèse de Cramér-Rao est vérifiée et l'on a

$$\begin{aligned} I_1(\lambda) &= -\mathbb{E}\left[ \frac{\partial^2}{\partial \lambda^2} \mathcal{L}\mathcal{L}(X_1; \lambda) \right] \\ &= -\mathbb{E}\left[ \frac{\partial^2}{\partial \lambda^2} \ln\left( \frac{\lambda^{X_1}}{X_1!} e^{-\lambda} \right) \right] \\ &= -\mathbb{E}\left[ \frac{\partial^2}{\partial \lambda^2} \left( X_1 \ln(\lambda) - \ln(X_1!) - \lambda \right) \right] \\ &= \frac{1}{\lambda^2} \mathbb{E}[X_1] \\ &= \frac{1}{\lambda}. \end{aligned}$$

Pour cet exemple également, l'information sur la moyenne $\lambda$ est d'autant plus grande que la variance (égale à $\lambda$) est petite.

**Densité translatée.** Supposons que la variable mère a pour densité

$$f(x) = e^{-(x-\theta)} \mathbb{1}_{[\theta,+\infty[}.$$

Il s'agit de la densité d'une [[Loi exponentielle|loi exponentielle translatée]]. Dans ce cas, l'hypothèse de Cramér-Rao n'est pas satisfaite : pour calculer la quantité d'information, on utilise directement la définition de $I_n(\theta)$.

# Remarque

Le support d'une loi de Poisson est l'ensemble des entiers naturels $\mathbb{N}$, et non $\mathbb{R}^+$ : les valeurs prises par $X$ sont nécessairement entières, comme le rappelle la factorielle $X_1!$ dans l'expression de la vraisemblance. Ce support ne dépend pas du paramètre $\lambda$, de sorte que l'hypothèse de Cramér-Rao reste satisfaite.

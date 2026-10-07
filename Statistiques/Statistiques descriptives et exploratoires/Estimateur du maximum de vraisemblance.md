# Définition

Soient $X = (X_1, \dots, X_n)$ des variables aléatoires de $\mathbb{R}^d$ et $p(x; \theta)$ leur densité. La [[Fonction de vraisemblance|vraisemblance]] est la densité jointe des observations, vue comme une fonction $\theta \to p(x; \theta)$.

L'[[Estimateur|estimateur]] du maximum de vraisemblance $\hat{\theta}(X)$, obtenu par la [[Méthode du maximum de vraisemblance]], est tel que

$$p(x; \hat{\theta}(X)) \geq \max_{\theta \in \Theta} p(x; \theta)$$

et, si $p(x; \theta)$ est dérivable, il est donné par

$$\frac{\partial p(x; \theta)}{\partial \theta} = 0.$$

# Interprétation

L'estimateur du maximum de vraisemblance cherche le meilleur ajustement des échantillons (d'entraînement), en supposant que les observations étaient les plus probables.

# Propriétés

En pratique, on utilise souvent

$$\frac{\partial \ln p(x; \theta)}{\partial \theta} = 0.$$

De plus, si les $X_i$ sont i.i.d., alors

$$\ln p(x; \theta) = \sum \ln p(x_i; \theta).$$

L'estimation par maximum de vraisemblance est liée à l'[[Estimateur sans biais de variance minimale|estimation sans biais de variance minimale]] et aux [[Méthode des moments|estimateurs des moments]] :

- S'il existe une [[Statistique suffisante|statistique suffisante]] $U$, l'estimateur du maximum de vraisemblance dépend d'elle :

$$p(x, \theta) = g(u, \theta)h(x)$$

$$\frac{\partial \ln p(x, \theta)}{\partial \theta} = \frac{\partial \ln g(u, \theta)}{\partial \theta}$$

$$\text{donc } \hat{\theta} = f(u)$$

- Si $\hat{\theta}$ est l'estimateur du maximum de vraisemblance de $\theta$, alors $f(\hat{\theta})$ est l'estimateur du maximum de vraisemblance de $f(\theta)$.
- L'estimation par maximum de vraisemblance est asymptotiquement [[Estimateur efficace|efficace]], c'est-à-dire que sa variance tend vers l'inverse de l'[[Information de Fisher|information de Fisher]] :

$$\mathbb{V}[\hat{\theta}_n] \to \frac{1}{I_n(\theta)}.$$

- Pour la famille exponentielle, les estimations par maximum de vraisemblance sont égales aux estimations par la [[Méthode des moments|méthode des moments]].

# Exemple

On suppose $X_i \sim \mathcal{N}(\mu, \sigma^2)$, c'est-à-dire que les $X_i$ suivent une [[Loi gaussienne|loi gaussienne]]. La log-vraisemblance est donnée par

$$\ln p(x; \mu, \sigma^2) = -\frac{n}{2} \ln(2\pi) - \frac{n}{2} \ln(\sigma^2) - \frac{1}{2\sigma^2} \sum_{i=1}^n (x_i - \mu)^2$$

Les équations du maximum de vraisemblance sont données par

$$\frac{\partial \ln p(x; \mu, \sigma^2)}{\partial \mu} = 0$$

$$\frac{\partial \ln p(x; \mu, \sigma^2)}{\partial \sigma^2} = 0$$

pour lesquelles les solutions sont données par

$$\hat{\mu} = \frac{1}{n} \sum_{i=1}^n X_i$$

$$\hat{\sigma}^2 = \frac{1}{n} \sum_{i=1}^n (X_i - \hat{\mu})^2$$

L'estimateur $\hat{\mu}$ est la [[Moyenne empirique|moyenne empirique]] et $\hat{\sigma}^2$ la [[Variance empirique|variance empirique]].

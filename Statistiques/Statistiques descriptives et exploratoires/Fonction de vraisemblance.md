# Définition

Soit un échantillon $(x_1, \dots, x_n)$ issu de la loi d'une [[Variable aléatoire|variable aléatoire]] $X$ et soit $\theta$ un paramètre à estimer. La **fonction de vraisemblance** de l'[[Échantillon et échantillonnage|échantillon]] est

$$\mathcal{L}(x_1,\ldots,x_n;\theta)=
\begin{cases}
f_{X_1,\ldots,X_n}(x_1,\ldots,x_n) & \text{si } X \text{ admet une densité},\\
\mathbb{P}[X_1=x_1,\ldots,X_n=x_n] & \text{si } X \text{ est à valeurs discrètes}.
\end{cases}$$

# Remarque

Les variables aléatoires $X_1, \dots, X_n$ étant [[Indépendance de variables aléatoires|indépendantes]] et de même loi que $X$, la vraisemblance peut s'écrire

- pour $X$ de [[Probabilité à densité|densité]] $f$ :

$$\mathcal{L}(x_1, \dots, x_n; \theta) = \prod_{i=1}^n f(x_i)$$

- pour $X$ à valeurs discrètes :

$$\mathcal{L}(x_1, \dots, x_n; \theta) = \prod_{i=1}^n \mathbb{P}[X = x_i].$$

La maximisation de cette fonction fait l'objet de la [[Méthode du maximum de vraisemblance]] et conduit à l'[[Estimateur du maximum de vraisemblance]].

# Propriétés

Par commodité, on considère la **log-vraisemblance**, définie par

$$\begin{aligned} \mathcal{L}\mathcal{L}(x_1, \dots, x_n; \lambda) &= \ln(\mathcal{L}(x_1, \dots, x_n; \lambda)) \\ &= \sum_{i=1}^n \ln(\mathbb{P}[X = x_i]) \\ &= -n\lambda + (x_1 + \dots + x_n)\ln\lambda - \sum_{i=1}^n \ln(x_i!) \end{aligned}$$

La fonction $x \to \ln(x)$ étant croissante, la vraisemblance et la log-vraisemblance sont maximales pour les mêmes valeurs de $\lambda$. Il est ainsi plus aisé de résoudre l'équation (par rapport à $\lambda$)

$$\frac{\partial}{\partial \lambda} \mathcal{L}\mathcal{L}(x_1, \dots, x_n; \lambda) = 0$$

que

$$\frac{\partial}{\partial \lambda} \mathcal{L}(x_1, \dots, x_n; \lambda) = 0.$$

# Exemple

Supposons que l'on dispose d'une observation $x_1$ d'une [[Loi gaussienne|loi gaussienne]] de variance connue $\sigma^2 = 0.4$ et de moyenne $\theta$ inconnue. Les densités gaussiennes considérées, notées $f_\theta(x)$, de variance $\sigma^2 = 0.4$ et de moyenne $\theta$ fluctuant entre 0 et 3, s'écrivent

$$f_\theta(x) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x-\theta)^2}{2\sigma^2}}$$

Selon la valeur de $\theta$, la probabilité d'observer $x_1$ est plus ou moins grande, et la loi gaussienne qui a le plus vraisemblablement généré $x_1$ est celle de densité $f_\theta$ avec $\theta = x_1$. On retrouve ce résultat en cherchant pour quelle valeur de $\theta$ la vraisemblance

$$\theta \to \mathcal{L}(x_1; \theta) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x_1-\theta)^2}{2\sigma^2}}$$

est maximale.

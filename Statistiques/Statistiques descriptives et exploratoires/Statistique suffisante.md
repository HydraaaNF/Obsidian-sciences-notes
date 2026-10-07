# Définition

Une **statistique suffisante** est une [[Statistique|statistique]] qui contient toute l'information portée par l'[[Échantillon et échantillonnage|échantillon]] $X_1, X_2, \ldots, X_n$ sur le paramètre $\theta$. Elle est aussi dite **exhaustive**.

On note :

- $L(x_1, x_2, \ldots, x_n; \theta)$ la densité ou fonction de masse de $(X_1, \ldots, X_n)$,
- $T$ une statistique dont la densité ou fonction de masse est donnée par $g(t; \theta)$.

# Interprétation

Si, lorsque $T$ est connu, la densité conditionnelle de $(X_1, \ldots, X_n)$ sachant $T$ ne dépend plus de $\theta$, alors $T$ porte toute l'information concernant $\theta$ : connaître $T$ suffit, l'observation détaillée de l'échantillon n'apportant pas d'information supplémentaire sur $\theta$.

Le critère pratique correspondant est donné par le [[Théorème de factorisation de Fisher]] : $T$ est une statistique suffisante si $L(\mathbf{x}, \theta) = g(t, \theta)h(\mathbf{x})$.

# Exemple

Pour une [[Loi gaussienne|loi gaussienne]] de moyenne $m$ connue et d'écart-type $\sigma$ inconnu, la densité jointe de l'échantillon s'écrit

$$L(\mathbf{x}, \sigma) = \frac{1}{(\sigma\sqrt{2\pi})^n} \exp\left(-\frac{1}{2\sigma^2}\sum_{i=1}^n (x_i - m)^2\right).$$

La statistique $T = \sum_{i=1}^n (X_i - m)^2$ est suffisante : on montre que $T/\sigma^2$ suit une [[Loi du chi-deux|loi du chi-deux]] à $n$ degrés de liberté, c'est-à-dire $T/\sigma^2 \sim \chi_n^2$, et donc que $L(\mathbf{x}, \sigma) = g(t, \sigma)h(\mathbf{x})$.

Pour la [[Loi de Poisson|loi de Poisson]] de paramètre $\lambda$ inconnu, la densité jointe s'écrit

$$L(\mathbf{x}, \lambda) = \exp(-n\lambda)\,\frac{\lambda^{\sum_{i=1}^n x_i}}{\prod_{i=1}^n x_i!}.$$

La statistique $S = \sum_{i=1}^n X_i$ est suffisante et $S \sim \mathcal{P}(n\lambda)$.

Pour la [[Loi gamma|loi gamma]] $\gamma_\theta$, la densité vérifie

$$\ln f(x, \theta) = -x + (\theta - 1)\ln(x) - \ln(\Gamma(\theta)),$$

et la statistique $\sum_{i=1}^n \ln(X_i)$ est suffisante d'après le [[Théorème de Darmois]].

Autres exemples de statistiques suffisantes :

- loi de [[Loi de Bernoulli|Bernoulli]] de paramètre $p$ : $\sum_{i=1}^n X_i$ ;
- loi gaussienne, $m$ inconnue et $\sigma$ connue : $\sum_{i=1}^n X_i$ ;
- loi gaussienne, $m$ connue et $\sigma$ inconnue : $\sum_{i=1}^n (X_i - m)^2$ ;
- loi gaussienne, $m$ et $\sigma$ inconnues : $(\overline{X}, S^2)$, où $\overline{X}$ est la [[Moyenne empirique|moyenne empirique]] et $S^2$ la [[Variance empirique|variance empirique]] ;
- loi de [[Loi exponentielle|exponentielle]] : $\sum_{i=1}^n X_i$.

# Remarque

- Le [[Théorème de factorisation de Fisher]] permet de dire si une statistique donnée est suffisante, mais il n'indique pas comment en trouver une.
- La notion de statistique suffisante est liée à la recherche d'un [[Estimateur sans biais de variance minimale]].
- Dans la densité jointe de $n$ variables gaussiennes indépendantes, le facteur de normalisation est $(\sigma\sqrt{2\pi})^n$ et l'exposant de l'exponentielle somme les écarts de toutes les observations : c'est cette forme qui assure que l'intégrale de la densité sur $\mathbb{R}^n$ vaut $1$. Un facteur de normalisation de la forme $\sigma^n\sqrt{n2\pi}$, ou une exponentielle qui ne porte que sur une seule observation, est une erreur fréquente.

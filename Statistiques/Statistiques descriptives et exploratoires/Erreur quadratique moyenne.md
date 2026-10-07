# Définition

Pour mesurer la précision d'un [[Estimateur|estimateur]] $T$ d'un paramètre $\theta$, on considère la [[Distance en moyenne d'ordre p|distance en moyenne quadratique]] : l'objectif est de choisir un estimateur $T$ minimisant la quantité

$$\|T - \theta\|_2^2 = \mathbb{E}\left[(T - \theta)^2\right],$$

appelée *erreur quadratique moyenne*.

# Propriétés

L'erreur quadratique moyenne se décompose en la [[Variance et écart-type|variance]] de l'estimateur et le carré de son [[Biais d'un estimateur|biais]] :

$$\mathbb{E}\left[(T - \theta)^2\right] = \mathbb{V}(T) + (\mathbb{E}[T] - \theta)^2.$$

En notant $b = \mathbb{E}[T] - \theta$ ce biais, l'erreur quadratique moyenne s'écrit $\mathbb{E}\left[(T - \theta)^2\right] = \mathbb{V}(T) + b^2$. Par conséquent, entre deux estimateurs sans biais, le plus précis est celui de variance minimale.

### Démonstration

Appelons le biais $b = \mathbb{E}[T] - \theta$, qui est une constante. On a

$$\begin{aligned} \mathbb{E}\left[(T-\theta)^2\right] &= \mathbb{E}\left[(T-\mathbb{E}[T]+\mathbb{E}[T]-\theta)^2\right] \\ &= \mathbb{E}\left[(T-\mathbb{E}[T]+b)^2\right] \\ &= \mathbb{E}\left[(T-\mathbb{E}[T])^2\right] + 2b\mathbb{E}[T-\mathbb{E}[T]] + b^2 \\ &= \mathbb{E}\left[(T-\mathbb{E}[T])^2\right] + b^2 \qquad \text{car } \mathbb{E}[T-\mathbb{E}[T]] = 0 \\ &= \mathbb{V}(T) + b^2 \\ &= \mathbb{V}(T) + (\mathbb{E}[T] - \theta)^2. \end{aligned}$$

# Exemple

La [[Moyenne empirique|moyenne empirique]] $\overline{X}$ est un estimateur sans biais de l'[[Espérance d'une variable aléatoire|espérance]] $\mathbb{E}[X]$ et sa variance vaut

$$\mathbb{V}(\overline{X}) = \frac{\sigma^2}{n},$$

lorsque la loi mère admet un moment d'ordre 2. Ainsi, l'erreur quadratique moyenne diminue lorsque la taille d'échantillon grandit :

$$\mathbb{E}\left[(\overline{X} - \mathbb{E}[X])^2\right] = \frac{\sigma^2}{n} \xrightarrow{n \to +\infty} 0.$$

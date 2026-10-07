# Définition

La **variance** d'une variable aléatoire $X$ est définie par

$$\mathbb{V}[X] = \sigma^2 = \mathbb{E}\left[(X - \mathbb{E}[X])^2\right] = \mathbb{E}[X^2] - \mathbb{E}[X]^2$$

où $\mathbb{E}[X]$ est l'[[Espérance d'une variable aléatoire|espérance]] de $X$. La racine carrée de la variance, notée $\sigma$, est l'**écart-type** :

$$\sigma = \sqrt{\mathbb{V}[X]}.$$

La variance est le [[Moment d'ordre k|moment centré d'ordre 2]].

# Propriétés

Pour toute variable aléatoire $X$ et tout réel $a$ :

- $\mathbb{E}\left[(X - a)^2\right] = \mathbb{V}[X] + \left(\mathbb{E}[X] - a\right)^2$
- $\mathbb{V}[X - a] = \mathbb{V}[X]$
- $\mathbb{V}[aX] = a^2\, \mathbb{V}[X]$

L'écart-type intervient dans l'[[Inégalité de Bienaymé-Tchebychev]], qui majore la probabilité que $X$ s'écarte de son espérance de plus de $k\sigma$.

# Remarque

Pour la variance d'une somme de variables aléatoires, voir [[Variance d'une somme de variables aléatoires]].

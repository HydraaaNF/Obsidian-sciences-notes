# Définition

Soient $(\Omega, \mathcal{F}, \mathbb{P})$ un [[Espace probabilisé|espace probabilisé]], $X$ une [[Variable aléatoire discrète|variable aléatoire réelle discrète]] définie sur $\Omega$ et $n \in \mathbb{N}$. Lorsque

$$\sum_{k \in X(\Omega)} \left|k\right|^n \mathbb{P}(X = k) < +\infty$$

on dit que $X$ **admet un moment d'ordre** $n$. Le moment d'ordre $n$ est alors le réel

$$\mathbb{E}(X^n) = \sum_{k \in X(\Omega)} k^n \mathbb{P}(X = k) < +\infty.$$

# Remarque

- Le **moment centré d'ordre $k$** s'obtient en centrant la variable : c'est le réel $\mathbb{E}\left[(X - \mathbb{E}(X))^k\right]$, étudié dans [[Moment centré d'ordre k]] ; le moment centré d'ordre 2 est la [[Variance]].
- Les moments centrés normalisés typiques sont la **skewness** (asymétrie) et le **kurtosis** (aplatissement) : voir [[Asymétrie et aplatissement]].

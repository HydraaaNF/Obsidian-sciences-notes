# Définition

Soient $(\Omega, \mathcal{F}, \mathbb{P})$ un [[Espace probabilisé|espace probabilisé]], $X$ une [[Variable aléatoire discrète|variable aléatoire réelle discrète]] définie sur $\Omega$ et $n \in \mathbb{N}$. Lorsque

$$\sum_{k \in X(\Omega)} \left|k\right|^n \mathbb{P}(X = k) < +\infty$$

on dit que $X$ **admet un moment d'ordre** $n$. Le moment d'ordre $n$ est alors le réel

$$\mathbb{E}(X^n) = \sum_{k \in X(\Omega)} k^n \mathbb{P}(X = k) < +\infty.$$

# Remarque

- Le **moment centré d'ordre $k$** s'obtient en centrant la variable : c'est le réel $\mathbb{E}\left[(X - \mathbb{E}(X))^k\right]$, étudié dans [[Moment centré d'ordre k]] ; le moment centré d'ordre 2 est la [[Variance]].
- Une autre convention réserve le nom de « moment d'ordre $k$ » au moment centré $\mu_k = \mathbb{E}\left[(X - \mathbb{E}(X))^k\right]$ et range la variance sous ce nom ; elle s'écrit alors aussi sous forme normalisée $\mu_k / \sigma^k$, où $\sigma$ est l'[[Variance|écart-type]]. Dans cette note, le moment d'ordre $n$ reste le moment brut $\mathbb{E}(X^n)$, et le moment centré porte son nom complet.
- Les moments centrés normalisés typiques sont la **skewness** (asymétrie) et le **kurtosis** (aplatissement) : voir [[Asymétrie et aplatissement]].

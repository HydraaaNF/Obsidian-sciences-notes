#adm-0 #adm-1

# Définition

Soient $(\Omega, \mathcal{F}, \mathbb{P})$ un [[Espace probabilisé|espace probabilisé]], $X$ une [[Variable aléatoire discrète|variable aléatoire réelle discrète]] définie sur $\Omega$ et $n \in \mathbb{N}$. Lorsque

$$\sum_{k \in X(\Omega)} \left|k\right|^n \mathbb{P}(X = k) < +\infty$$

on dit que $X$ **admet un moment d'ordre** $n$. Le moment d'ordre $n$ est alors le réel

$$\mathbb{E}(X^n) = \sum_{k \in X(\Omega)} k^n \mathbb{P}(X = k) < +\infty.$$

# Remarque

- Une autre convention réserve le nom de « moment d'ordre $k$ » au moment centré $\mu_k = \mathbb{E}\left[(X - \mathbb{E}(X))^k\right]$ et range la variance sous ce nom ; elle s'écrit alors aussi sous forme normalisée $\mu_k / \sigma^k$, où $\sigma$ est l'[[Variance|écart-type]]. Dans cette note, le moment d'ordre $n$ reste le moment brut $\mathbb{E}(X^n)$, et le moment centré porte son nom complet.
- Les moments centrés normalisés typiques sont la **skewness** (asymétrie) et le **kurtosis** (aplatissement) : voir [[Asymétrie et aplatissement]].

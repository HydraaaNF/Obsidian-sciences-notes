# Définition

Soient $X_1, \ldots, X_n$ des [[Variable aléatoire discrète|variables aléatoires discrètes]] [[Indépendance de variables aléatoires|indépendantes]] et identiquement distribuées, à valeurs dans $[1, K]$. La proportion empirique (ou fréquence empirique) de l'événement $k$ (ou, de façon équivalente, de la probabilité $p_k = \mathbb{P}[X = k]$) est estimée par la [[Statistique|statistique]]

$$F_k = \frac{1}{n} \sum_{i=1}^n \delta(X_i = k)$$

où $\delta(X_i = k) = 1$ si $X_i = k$ et $0$ sinon.

# Propriétés

$F_k$ est une [[Variable aléatoire|variable aléatoire]], puisque toute fonction de variables aléatoires est une variable aléatoire. L'[[Espérance d'une variable aléatoire|espérance]] et la [[Variance|variance]] de $F_k$ valent

$$\mathbb{E}[F_k] = p_k$$

$$\mathbb{V}[F_k] = \frac{p_k(1-p_k)}{n}$$

D'après le [[Théorème de la limite centrale]], $F$ [[Convergence en loi|converge en loi]] vers la [[Loi gaussienne|loi gaussienne]] :

$$F \to \mathcal{N}\left(p, \sqrt{\frac{p(1-p)}{n}}\right)$$

# Remarque

La proportion empirique est un cas particulier de la [[Moyenne empirique]] : c'est la moyenne empirique des indicatrices $\delta(X_i = k)$.

C'est l'[[Estimateur|estimateur]] utilisé pour construire l'[[Intervalle de confiance d'une proportion]].

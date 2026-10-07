# Théorèmes

Le théorème de transfert, admis, permet de calculer l'[[Espérance d'une variable aléatoire|espérance]] de $g \circ X$, notée abusivement $g(X)$ et dite « fonction de la variable aléatoire $X$ », sans connaître la [[Loi d'une variable aléatoire|loi]] de $g(X)$ mais seulement celle de $X$ : c'est très utile en pratique.

**Cas discret.** Soient $(\Omega, \mathcal{F}, \mathbb{P})$ un [[Espace probabilisé|espace probabilisé]], $X$ une [[Variable aléatoire discrète|variable aléatoire réelle discrète]] définie sur $\Omega$, et $g$ une fonction définie sur $X(\Omega)$ à valeurs réelles. Si

$$\sum_{k \in X(\Omega)} |g(k)| \, \mathbb{P}(X = k) < +\infty$$

alors la variable aléatoire réelle $g \circ X$, notée $g(X)$, a une espérance et l'on a

$$\mathbb{E}(g(X)) = \sum_{k \in X(\Omega)} g(k) \, \mathbb{P}(X = k)$$

**Cas général.** Soient $(\Omega, \mathcal{F}, \mathbb{P})$ un espace probabilisé, $X$ une [[Variable aléatoire réelle|variable aléatoire réelle]] définie sur $\Omega$, et $g$ une fonction (mesurable) définie sur $X(\Omega)$ à valeurs réelles. Si

$$\int_{\mathbb{R}} |g(x)| \, \mathrm{d}p_X(x) < +\infty$$

alors la variable aléatoire réelle $g(X)$ a une espérance et l'on a

$$\mathbb{E}(g(X)) = \int_{\mathbb{R}} g(x) \, \mathrm{d}p_X(x)$$

où $p_X$ désigne la [[Loi d'une variable aléatoire|loi de probabilité]] de $X$.

# Propriétés

**Fonction de répartition de $g(X)$.** Soient $X = (X_1, \dots, X_n)$ un [[Vecteur aléatoire|vecteur aléatoire]] de $\mathbb{R}^n$ et $g : X(\Omega) \to \mathbb{R}$ mesurable. La fonction de répartition de $g(X)$ est

$$F_{g(X)}(t) = \int_{\{x \in \mathbb{R}^n;\, g(x) \leq t\}} \mathrm{d}p_X(x).$$

En particulier, si $X$ admet une densité $f_X$,

$$F_{g(X)}(t) = \int_{\{x \in \mathbb{R}^n;\, g(x) \leq t\}} f_X(x) \, \mathrm{d}x.$$

# Exemple

Si $X$ suit la [[Loi de Poisson|loi de Poisson]] de paramètre $\lambda$, la variable aléatoire $Y = \frac{1}{X+1}$ est définie et positive sur $\Omega$, donc $Y = |Y|$ admet une espérance, finie ou infinie, que l'on peut calculer à l'aide du théorème de transfert appliqué à la fonction $g : x \mapsto \frac{1}{x+1}$. On obtient :

$$\begin{aligned}
\mathbb{E}(Y) &= \mathbb{E}(g(X)) = \sum_{k \in \mathbb{N}} \frac{1}{k+1} \, \mathbb{P}(X = k) = \sum_{k=0}^{+\infty} \frac{1}{k+1} e^{-\lambda} \frac{\lambda^k}{k!} \\
&= e^{-\lambda} \frac{1}{\lambda} \sum_{k=0}^{+\infty} \frac{\lambda^{k+1}}{(k+1)!} = e^{-\lambda} \frac{1}{\lambda} \sum_{k=1}^{+\infty} \frac{\lambda^k}{k!} \\
&= e^{-\lambda} \frac{1}{\lambda} (e^\lambda - 1) = \frac{1}{\lambda} (1 - e^{-\lambda})
\end{aligned}$$

# Remarque

Le théorème de transfert admet une version pour les vecteurs aléatoires : voir [[Théorème de transfert pour un vecteur aléatoire]].

L'[[Espérance d'une variable aléatoire|espérance]] d'une variable aléatoire réelle correspond au cas particulier $g = \mathrm{Id}$ du théorème de transfert.

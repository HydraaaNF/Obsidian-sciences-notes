# Énoncé
## Cas discret
Soient $(\Omega, \mathcal{F}, \mathbb{P})$ un espace probabilisé, $X$ une variable aléatoire réelle discrète définie sur $\Omega$ et $g$ une fonction définie sur $X(\Omega)$ à valeurs réelles. Si $$\sum_{k \in X(\Omega)} \left| g(k) \right| \mathbb{P}(X = k) < +\infty$$ alors la variable aléatoire réelle $g \circ X$, notée $g(X)$, a une espérance et l'on a $$\mathbb{E}(g(X)) = \sum_{k \in X(\Omega)} g(k) \mathbb{P}(X = k)$$
## Cas continue
Soit $X = (X_1, ..., X_n)$ un vecteur aléatoire de $\mathbb{R}^n$ et soit $g : X(\Omega) \to \mathbb{R}$ (mesurable). On suppose que la variable aléatoire réelle $g(X)$ est positive ou intégrable (de sorte que $\mathbb{E}(g(X))$ existe). Alors $$\mathbb{E}(g(X)) = \int_{\mathbb{R}^n} g(X)dp_X(x) \ $$
# Corollaire
Soit $X = (X_1, ..., X_n)$ un vecteur aléatoire de $\mathbb{R}^n$ et soit $g : X(\Omega) \to \mathbb{R}$ (mesurable). Alors la fonction de répartition de $g(X)$ est $$F_{g(X)}(t) = \int_{x \in \mathbb{R}^n; g(X) \leq t} \ dp_X(x)$$En particulier, si $X$ admet une densité, on a $$F_{g(X)}(t) = \int_{x \in \mathbb{R}^n; g(X) \leq t} f_X(x) \ dx$$

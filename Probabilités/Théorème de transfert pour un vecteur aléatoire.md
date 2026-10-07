# Théorème

Pour déterminer la loi, ou simplement l'[[Espérance d'une variable aléatoire|espérance]], de la v.a.r. $g(X_1, \dots, X_n)$ en utilisant seulement la [[Loi d'un vecteur aléatoire|loi conjointe]] de $X_1, \dots, X_n$, on utilise le théorème de transfert (admis) :

Soit $X = (X_1, \dots, X_n)$ un [[Vecteur aléatoire|vecteur aléatoire]] de $\mathbb{R}^n$ et soit $g : X(\Omega) \rightarrow \mathbb{R}$ (mesurable). On suppose que la v.a.r. $g(X)$ est positive ou intégrable (de sorte que $\mathbb{E}(g(X))$ existe). Alors

$$\mathbb{E}(g(X)) = \int_{\mathbb{R}^n} g(x) dp_X(x)$$

où $p_X$ désigne la [[Loi d'un vecteur aléatoire|loi]] du vecteur aléatoire $X$.

Ce résultat ne fait que généraliser le [[Théorème de transfert]] énoncé dans le cas où $X$ est une v.a. à valeurs réelles. Ici, l'intégrale est multiple :

$$\mathbb{E}(g(X_1 \dots X_n)) = \int_{\mathbb{R}^n} g(x_1, \dots, x_n) dp_{(X_1, \dots, X_n)}(x_1, \dots, x_n)$$

# Exemple

Soit $(X, Y)$ un couple aléatoire de [[Loi uniforme sur un domaine|loi uniforme]] sur le disque $D_R$ de centre $(0, 0)$ et de rayon $R$. Quelle est la valeur de $\mathbb{E}(X^2 + Y^2)$ ?

Le couple étant uniforme sur $D_R$, sa densité est $f_{(X,Y)}(x, y) = \frac{1}{\pi R^2} \mathbf{1}_{D_R}(x, y)$. $X^2 + Y^2$ est positive, donc son espérance existe (mais elle peut être égale à $+\infty$). D'après le théorème de transfert, on a

$$\begin{aligned} \mathbb{E}(X^2 + Y^2) &= \iint_{\mathbb{R}^2} (x^2 + y^2) f_{(X,Y)}(x, y) dxdy \\ &= \frac{1}{\pi R^2} \iint_{D_R} (x^2 + y^2) dxdy \\ &= \frac{1}{\pi R^2} \int_0^R \int_0^{2\pi} r^2 r d\theta dr \\ &= \frac{1}{\pi R^2} 2\pi \int_0^R r^3 dr \\ &= \frac{R^2}{2} \end{aligned}$$

# Remarque

Pour déterminer la loi de $g(X)$, et non seulement son espérance, voir [[Loi d'une fonction d'un vecteur aléatoire]].

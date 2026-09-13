# Loi
Soit $\alpha > 0$ et $\beta > 0$. Une variable aléatoire réelle $X$ suit la loi Gamma de paramètres $\alpha$ et $\beta$ si elle admet la densité $$f_X(x) = \frac{\beta^\alpha}{\Gamma(\alpha)} x^{\alpha-1} e^{-\beta x} \mathbb{1}_{\left]0, +\infty \right[}(x)$$
# Propriétés
Soit $X \sim \Gamma(\alpha, \beta)$, alors :
- les moments de tout ordre existent
- $\mathbb{E}(X^k) = \frac{\alpha (\alpha + 1) ... (\alpha + k - 1)}{\beta^k}$ en particulier $\mathbb{E}(X) = \frac{\alpha}{\beta}$
- $\mathbb{V}(X) = \frac{\alpha}{\beta^2}$
- $\phi_X(\xi) = (\frac{\beta}{\beta - i \xi})^\alpha$

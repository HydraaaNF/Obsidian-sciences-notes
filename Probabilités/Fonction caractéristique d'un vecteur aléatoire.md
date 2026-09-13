# Définition
Soit $X$ un vecteur aléatoire de $\mathbb{R}^n$. Sa fonction caractéristique est définie pour $\xi \in \mathbb{R}^n$ par $$\phi_X(\xi) = \mathbb{E}(e^{iX \cdot \xi})$$
# Propriétés
- Si $X$ est un vecteur aléatoire continu, sa fonction caractéristique est la transformée de Fourier n-dimensionnelle de la densité $f_X$, i.e. $$\phi_X(\xi) = \int_{\mathbb{E}^n} e^{ix \cdot \xi} f_X(x) \ dx$$
- Soit $X = (X_1, ..., X_n)$ un vecteur aléatoire de $\mathbb{E}^n$ dont les coordonnées $X_i$ sont indépendantes. Alors $$\forall \xi = (\xi_1, ..., \xi_n) \in \mathbb{R}^n, \phi_X(\xi) = \phi_{X_1}(\xi_1)...\phi_{X_n}(\xi_n)$$
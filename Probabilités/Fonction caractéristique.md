# Définition
Soient $(\Omega, \mathcal{F}, \mathbb{P})$ un espace probabilisé et $X$ une variable aléatoire réelle définie sur $\Omega$. On appelle fonction caractéristique de $X$ la fonction $\phi_X$ définie sur $\mathbb{R}$ par $$\forall \xi \in \mathbb{R}, \phi_X(\xi) = \mathbb{E}(e^{i\xi X})$$
# Propriétés
- Si $X$ est continue, alors $\phi_X$ est la transformée de Fourier de la densité $f_X$ : $$\phi_X(\xi) = \int_\mathbb{R} f_X(x)e^{i\xi x} \ dx$$
- Si $X$ est discrète à valeurs dans $\mathbb{Z}$, alors $\phi_X$ est la transformée de Fourier discrète de la suite $(p_X(\{k\}))_{k \in \mathbb{Z}}$ :$$\phi_X(\xi) = \sum_{k \in \mathbb{z}} e^{i\xi k}p_X(\{k\})$$
- Soit $X$ une variable aléatoire réelle admettant un [[Moment d'ordre k|moment d'ordre]] $n \geq 1$. Alors $\phi_X$ est $n$ fois dérivable sur $\mathbb{R}$ et on a $$\forall k \in [\![0, n]\!], \mathbb{E}(X^k) = (-i)^k\phi_X^{(k)}(0)$$
- Soit $X_1, ..., X_n$ des variables aléatoires réelles [[Indépendance de variables aléatoires|indépendantes]], et soit $S = \sum_{i=1}^n X_i$. Alors $$\forall \xi \in \mathbb{R}, \phi_S(\xi) = \prod_{k=1}^n \phi_{X_k}(\xi)$$

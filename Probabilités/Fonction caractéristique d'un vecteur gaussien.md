# Théorème

Soit $X$ un [[Vecteur gaussien|vecteur gaussien]]. Sa [[Fonction caractéristique d'un vecteur aléatoire|fonction caractéristique]] est donnée par

$$\forall \xi \in \mathbb{R}^n \qquad \Phi_X(\xi) = e^{i\xi \cdot \mathbb{E}(X)} e^{-\frac{1}{2}\xi^T \mathbf{C}(X)\xi}$$

où $\xi$ est un vecteur colonne de $\mathbb{R}^n$, $\mathbb{E}(X)$ le [[Vecteur moyen|vecteur moyen]] de $X$ et $\mathbf{C}(X)$ sa [[Matrice de covariance|matrice de covariance]].

### Démonstration

On a

$$\Phi_X(\xi) = \mathbb{E}\left(e^{i \sum_{k=1}^n \xi_k X_k}\right) = \mathbb{E}\left(e^{i (\xi \cdot X)}\right)$$

Sous cette forme, on reconnaît $\Phi_{\xi \cdot X}(t)$, la [[Fonction caractéristique|fonction caractéristique]] de la [[Variable aléatoire réelle|variable aléatoire réelle]] $\xi \cdot X$, calculée au point $t = 1$. Or, $\xi \cdot X \sim \mathcal{N}(\mu_\xi, \sigma_\xi^2)$, avec $\mu_\xi = \xi \cdot \mathbb{E}(X)$ et $\sigma_\xi^2 = \xi^T \mathbf{C}(X) \xi$. La fonction caractéristique d'une [[Loi gaussienne|variable aléatoire gaussienne]] $\mathcal{N}(\mu, \sigma^2)$ est

$$t \mapsto e^{it\mu} e^{-\frac{1}{2}t^2\sigma^2}.$$

On en déduit le résultat en faisant $t = 1$.

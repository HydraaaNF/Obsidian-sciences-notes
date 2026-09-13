# Définition
Un vecteur aléatoire $X = (X_1, ..., X_n)$ est un vecteur gaussien de $\mathbb{R}^n$ si toute combinaison linéaire de ses coordonnées $X_1, ..., X_n$ est une variable aléatoire réelle gaussienne.

# Propriétés
- Soit $X$ un vecteur gaussien de $\mathbb{R}^n$ et $c$ un vecteur colonne de $\mathbb{R}^n$. Avec les notations $c \cdot X \sim \mathcal{N}(\mu_c, \sigma_c^2)$, on a
$$\mu_c = c \cdot \mathbb{E}(X)$$$$\sigma_c^2 = c^T \ C(X) \ c$$
- Soit $X$ un vecteur gaussien. Sa fonction caractéristique est donnée par $$\forall \xi \in \mathbb{R}^n, \phi_X(\xi) = e^{i\xi \cdot \mathbb{E}(X)} e^{-\frac{1}{2}\xi^T \ C(X) \ \xi}$$où $\xi$ est un vecteur colonne de $\mathbb{R}^n$.
- Soit $X$ un vecteur gaussien de $\mathbb{R}^n$, $A \in \mathcal{M}_{m, n}(\mathbb{R})$, et $B$ un vecteur colonne de $\mathbb{R}^m$. Alors $AX + B$ est un vecteur gaussien de $\mathbb{R}^m$ de vecteur moyen $A\mathbb{E}(X) + B$ et de matrice de covariance $A \ C(X) \ A^T$.
- Soit $X$ un vecteur gaussien de $\mathbb{R}^n$. On suppose que la matrice de covariance de $C(X)$ est **inversible**. Alors $X$ admet une densité, donnée par $$\forall x \in \mathbb{R}^n, f_X(x) = (2\pi)^{-\frac{n}{2}}(det \ C(X))^{-\frac{1}{2}}e^{-\frac{1}{2}(x - \mathbb{E}(X))^T \ C(X)^{-1} \ (x-\mathbb{E}(X))}$$
- Soit $X$ un vecteur gaussien non dégénéré. Les variables aléatoires réelles $X_1, ..., X_n$ sont indépendantes ssi $C(X)$ est diagonale.
- Soit $\vec{V} = \sum_{i=1}^n X_i e_i$ un vecteur gaussien, décomposé dans la base orthonormée $\{e_1, ..., e_n\}$ de $\mathbb{R}^n$. Il existe une base orthonormée $\{v_1, ..., v_n\}$ de $\mathbb{R}^n$ dans laquelle les coordonnées de $\vec{V}$ sont des variables aléatoires réelles indépendantes. Autrement dit $\vec{V} = \sum_{i=1}^n Y_i v_i$ avec $Y_1, ..., Y_n$ indépendantes.

# Procédé de décorrélation
Pour trouver $\{v_1, ..., v_n\}$ et $Y_1, ..., Y_n$, on diagonalise $C(X)$ et on en déduit une base orthonormée de vecteurs propres. Pour cela, on se souvient que deux vecteurs propres correspondant à deux valeurs propres distinctes sont automatiquement orthogonaux, car $C(X)$ est symétrique réelle, de sorte que si toutes les valeurs propres sont simples il suffit de normer les vecteurs propres, et sinon, on utilise le procédé de Gram-Schmidt au sein de chaque sous-espace propre correspondant à une valeur propre multiple. Les colonnes représentant, dans la base $\{e_1, ..., e_n\}$, ces vecteurs propres formant une base orthonormée constituent la matrice de passage orthogonale $P$. Il reste à poser $Y = P^TX$. 
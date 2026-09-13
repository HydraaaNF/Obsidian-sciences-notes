# Définition
Soit $X = (X_1, ..., X_n)$ un vecteur aléatoire de $\mathbb{R}^n$. La loi de $X$, ou distribution de probabilité de $X$, est la probabilité $p_X$ sur $(\mathbb{R}, \mathcal{B}(\mathbb{R}^n))$ définie par $$\forall B \in \mathcal{B}(\mathbb{R}^n), p_X(B) = \mathbb{P}(X^{-1}(B)) = \mathbb{P}(X \in B)$$On dit que $p_X$ est la loi conjointe des variables aléatoires réelles $X_1, ..., X_n$.

## Caractérisation
Pour connaître la loi $p_X$ d'un vecteur aléatoire $X = (X_1, ..., X_n)$ de $\mathbb{R}^n$, il suffit de connaître $$\mathbb{P}(X_1 \in \left]a_1, b_1\right[, ..., X_n \in \left]a_n, b_n\right[)$$pour tous réels $a_1, ..., a_n, b_1, ..., b_n$ tels que $a_1 < b_1, ... a_n < b_n$.

## Corollaire
Pour connaitre la loi $p_X$ d'un vecteur aléatoire $X=(X_1, ..., X_n)$ **discret**, il suffit de connaitre $$\mathbb{P}(X_1 = k_1, ..., X_n = k_n)$$pour tous les $(k_1, ..., k_n) \in X_1(\Omega) \times ... \times X_n(\Omega)$.
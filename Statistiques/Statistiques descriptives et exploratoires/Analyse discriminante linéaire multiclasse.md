# Définition
Soit $K$ classes de $n_i$ individus chacune, de moyenne $\mu_i$, et $\mu$ la moyenne globale.

**Matrice de dispersion intra-classe** :
$$S_w = \sum_{i=1}^{K}\sum_{j=1}^{n_i} (x_{ij}-\mu_i)(x_{ij}-\mu_i)^\top$$

**Matrice de dispersion inter-classes** :
$$S_b = \sum_{i=1}^{K} (\mu_i - \mu)(\mu_i-\mu)^\top$$

On cherche la projection $y = Ux$ qui maximise
$$\max_U \frac{|U^\top S_b U|}{|U^\top S_w U|}$$

dont la solution est donnée par le système aux valeurs propres généralisé $S_b u_k = \lambda_k S_w u_k$.

# Interprétation
Généralise le [[Discriminant linéaire de Fisher]] à plus de deux classes.

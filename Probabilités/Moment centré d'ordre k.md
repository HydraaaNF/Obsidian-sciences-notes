# Définition
Lorsque $X$ admet un [[Moment centré d'ordre k|moment d'ordre k]], on appelle moment centré d'ordre $k$ le réel $\mathbb{E}[(X - \mathbb{E}(X))^k]$.
Le moment centré d'ordre 2 s'appelle la variance de $X$ : $$\mathbb{V}(X) = \mathbb{E}[(X - \mathbb{E}(X))^2]$$
La racine carrée de la variance est l'écart-type de $X$ : $$\sigma_X = \sqrt{\mathbb{V}(X)}$$
# Propriétés
Soit $X$ admettant un moment d'ordre 2.
- $\mathbb{V}(X) \geq 0$.
- Si $\mathbb{V}(X)$ est nulle, $X$ est presque-sûrement constante.
- Soit $\alpha$ un réel, alors $\mathbb{V}(\alpha X) = \alpha^2\mathbb{V}(X)$.
- L'opérateur $\mathbb{V}$ est invariant par translation.
- $\mathbb{V}(X) = \mathbb{E}(X^2) - \mathbb{E}(X)^2$.
- Soit $X_1, ..., X_n$ des variables aléatoires réelles de carré intégrable. Alors $\mathbb{V}(\sum_{i=1}^n X_i) = \sum_{i=1}^n \mathbb{V}(X_i) + 2 \sum_{i \leq i < j \leq n} cov(X_i, X_j)$
- Soit $X_1, ..., X_n$ des variables aléatoires réelles de carré intégrable non corrélées deux à deux. Alors $\mathbb{V}(\sum_{i=1}^n X_i) = \sum_{i=1}^n \mathbb{V}(X_i)$

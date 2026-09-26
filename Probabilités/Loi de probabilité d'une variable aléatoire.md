# Définition
## Cas général
Soit $(\Omega, \mathcal{F}, \mathbb{P})$ un espace probabilisé et soit $X$ une variable aléatoire. La probabilité $p_X$ définie sur $\mathcal{B}(\mathbb{R})$ par $$\forall B \in \mathcal{B}(\mathbb{R}), p_X(B) = \mathbb{P}(X \in B) = \mathbb{P}(\{ \omega \in \Omega; X(\omega) \in B\})$$est appelée loi de probabilité de $X$.
## Cas discret
Soit  $(\Omega, \mathcal{F}, \mathbb{P})$ un espace probabilisé et soit $X : \Omega \to E$ une variable aléatoire **discrète**. La probabilité $p_X$ définie sur $\mathcal{P}(E)$ par $$\forall B \in \mathcal{P}(E), p_X(B) = \sum_{k \in B} \mathbb{P}(X = k)$$ où $\mathbb{P}(X = k) = \mathbb{P}(\{\omega \in \Omega; X(\omega) = k\})$, est appelée **loi de probabilité** de $X$.

## Cas continu
Si la loi de probabilité $p_X$ d'une variable aléatoire réelle $X$ est une probabilité absolument continue dont la densité est $f$, on dit que $X$ est une variable aléatoire continue de densité $f$. La densité $f$ de $X$ est notée $f_X$. On a donc $$\forall B \in \mathcal{B}(\mathbb{R}), p_X(B) = \mathbb{P}(X \in B) = \int_B f_X(x) \ dx$$
# Propriétés
- Soit $X$ et $Y$ des variables aléatoires réelles continues et [[Indépendance de variables aléatoires|indépendantes]]. Alors la variable aléatoire réelle $X+Y$ a pour densité $$f_{X+Y} = f_X * f_Y$$

# Définition
Soient $(\Omega, \mathcal{F}, \mathbb{P})$ un espace probabilisé et $X$ une variable aléatoire réelle définie sur $\Omega$ telle que $X(\Omega) \subset \mathbb{N}$. On appelle fonction génératrice de $X$ la fonction $G_X$ définie par $$G_X(z) = \mathbb{E}(x^X) = \sum_{n \in \mathbb{N}} \mathbb{P}(X = n)z^n$$ 
# Propriétés
- Soit $X$ et $Y$ des variables aléatoires réelles sur le même espace probabilisé et à valeurs dans $\mathbb{N}$. On suppose que $X$ et $Y$ sont **indépendantes**. Alors $$G_{X+Y}(z) = G_X(z)G_Y(z)$$
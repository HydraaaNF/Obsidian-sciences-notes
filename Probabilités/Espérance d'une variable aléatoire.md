# Définition
## Cas discret
Soient $(\Omega, \mathcal{F}, \mathbb{P})$ un espace probabilisé et $X$ une variable aléatoire réelle discrète définie sur $\Omega$. **L'espérance** de $X$, sous réserve d'existence, est : $$\mathbb{E}(X) = \sum_{k \in X(\Omega)} k\mathbb{P}(X = k)$$ Le nombre $\mathbb{E}(X)$ est également appelé **moyenne** de $X$.

# Propriétés
- L'espérance est linéaire. Autrement dit, si $X$ et $Y$ sont des variables aléatoires réelle discrètes définies sur le même espace probabilisé et admettant une espérance, on a, pour tous réels $\alpha$ et $\beta$ $$\mathbb{E}(\alpha X + \beta Y) = \alpha\mathbb{E}(X) + \beta\mathbb{E}(Y)$$
- L'espérance d'une variable aléatoire réelle discrète positive est positive.
- Si $X$ est une variable aléatoire discrète **positive** vérifiant $\mathbb{E}(X) = 0$, alors $X$ est presque-sûrement nulle.
- L'espérance d'une variable aléatoire réelle **constante** est égale à cette constante.
- Soit $X$ et $Y$ deux variables aléatoires réelles intégrables et **indépendantes**. Alors $XY$ est intégrable et $$\mathbb{E}(XY) = \mathbb{E}(X)\mathbb{E}(Y)$$

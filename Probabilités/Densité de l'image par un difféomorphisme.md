# Théorème

Soit $X$ une [[Variable aléatoire continue|variable aléatoire continue]] de [[Probabilité à densité|densité]] $f_X$ et $\phi$ une fonction différentiable monotone, c'est-à-dire un difféomorphisme de son domaine sur son image. Alors $Y = \phi(X)$ est une variable aléatoire continue de densité $f_Y$ donnée par

$$f_Y(y) = \frac{f_X(\phi^{-1}(y))}{|\phi'(\phi^{-1}(y))|}.$$

# Exemple

Pour la transformation $Y = \exp(X)$, on obtient

$$f_Y(y) = \frac{f_X(x)}{\exp(x)} = \frac{f_X(\ln(y))}{y}.$$

# Remarque

- La formule s'applique à toute densité $f_X$, par exemple à celle d'une [[Loi uniforme sur un domaine|loi uniforme sur un domaine]].
- Pour une fonction d'un vecteur aléatoire, voir [[Loi d'une fonction d'un vecteur aléatoire]].

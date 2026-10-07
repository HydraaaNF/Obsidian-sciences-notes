# Propriétés

Pour une variable aléatoire $X$ de densité $f$, l'espérance d'une fonction $\phi$ de $X$ est
$$\mathbb{E}[\phi(X)] = \int \phi(x) f(x)\,dx$$

Pour un couple $(X, Y)$ de densité jointe $f(x, y)$, l'espérance du produit $XY$ est
$$\mathbb{E}[XY] = \int \int xy\, f(x, y)\,dx\,dy$$

Si $X$ et $Y$ sont [[Indépendance de variables aléatoires|indépendantes]], alors
$$\mathbb{E}[XY] = \mathbb{E}[X]\mathbb{E}[Y]$$

# Remarque

L'égalité $\mathbb{E}[XY] = \mathbb{E}[X]\mathbb{E}[Y]$ équivaut à une [[Covariance]] nulle :
$$\operatorname{Cov}(X, Y) = \mathbb{E}[XY] - \mathbb{E}[X]\mathbb{E}[Y] = 0$$

Les variables $X$ et $Y$ sont alors dites [[Variables aléatoires non corrélées|non corrélées]] ; mais la réciproque de l'implication est fausse : deux variables non corrélées ne sont pas nécessairement indépendantes.

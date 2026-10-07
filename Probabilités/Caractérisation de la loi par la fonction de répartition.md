# Théorème

Deux [[Variable aléatoire réelle|variables aléatoires réelles]] ont même [[Loi d'une variable aléatoire|loi]] si et seulement si elles ont même [[Fonction de répartition|fonction de répartition]].

### Démonstration

Si deux variables aléatoires $X$ et $Y$ vérifient $p_X = p_Y$, on a évidemment :

$$F_X(t) = p_X(] -\infty, t]) = p_Y(] -\infty, t]) = F_Y(t)$$

Réciproquement, supposons $F_X = F_Y$. La [[Tribu borélienne|tribu borélienne]] $\mathcal{B}(\mathbb{R})$ peut être engendrée à l'aide des seuls intervalles de la forme $] -\infty, t]$. Par conséquent connaître une probabilité $p$ sur ces intervalles permet de la connaître partout sur $\mathcal{B}(\mathbb{R})$ (par $\sigma$-additivité). Ainsi, connaître la fonction de répartition de $X$ permet de connaître la loi $p_X$ de $X$, i.e. $F_X$ caractérise $p_X$.

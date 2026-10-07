# Définition

Soient $X$ et $Y$ deux [[Variable aléatoire|variables aléatoires]]. L'**espérance conditionnelle** de $X$ sachant $Y = y$ est définie par

$$\mathbb{E}[X|Y = y] = \sum_x x\, p_{X|Y}(x|y), \quad \text{quand } p_Y(y) > 0$$

dans le cas discret, et par

$$\mathbb{E}[X|Y = y] = \int_{-\infty}^{\infty} x\, f_{X|Y}(x|y)\, dx, \quad \text{quand } f_Y(y) > 0$$

dans le cas continu. Ici $p_{X|Y}$ et $f_{X|Y}$ désignent les [[Lois marginales|lois conditionnelles]] de $X$ sachant $Y$, et $p_Y$, $f_Y$ les lois marginales de $Y$. Dans les deux cas, l'espérance conditionnelle est une fonction de $y$.

# Propriétés

## Formule de l'espérance totale

L'[[Espérance d'une variable aléatoire|espérance]] de $X$ est la moyenne de ses espérances conditionnelles sachant $Y = y$, pondérée par la loi de $Y$ :

$$\mathbb{E}[X] = \sum_y \mathbb{E}[X|Y = y]\, p_Y(y) = \mathbb{E}_Y[\mathbb{E}[X|Y]]$$

## Indépendance

Si $X$ et $Y$ sont [[Indépendance de variables aléatoires|indépendantes]], l'espérance conditionnelle de $X$ sachant $Y = y$ ne dépend pas de $y$ :

$$\mathbb{E}[X|Y = y] = \mathbb{E}[X]$$

# Remarque

- Dans le cas discret, la loi conditionnelle s'évalue en $x$ sachant $y$ : la forme correcte est $p_{X|Y}(x|y)$. L'écriture $p_{X|Y}(x, y)$ est une erreur fréquente, car elle sépare les deux arguments par une virgule comme pour une loi jointe, alors que $y$ est la condition.
- La formule de l'espérance totale est l'analogue de la [[Formule des probabilités totales]] : les espérances conditionnelles y remplacent les [[Probabilité conditionnelle|probabilités conditionnelles]].

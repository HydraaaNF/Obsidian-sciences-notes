# Définition
Soient $X$ et $Y$ deux variables aléatoires.

## Cas discret
$$p_{Y|X}(y|x) = \mathbb{P}(Y=y|X=x) = \frac{p_{X,Y}(x,y)}{p_X(x)} = \frac{p_{X,Y}(x,y)}{\sum_y p_{X,Y}(x,y)}$$
défini pour tout $x$ tel que $p_X(x) > 0$.

## Cas continu
$$f_{Y|X}(y|x) = \frac{f_{X,Y}(x,y)}{f_X(x)}$$
où $f_X(x) = \int_{-\infty}^{+\infty} f_{X,Y}(x,y)\,dy$ est la densité [[Lois marginales|marginale]] de $X$. Le rapport définit une densité conditionnelle pour presque tout $x$ : il est déterminé partout où $f_X(x) > 0$, et ses valeurs sur l'ensemble $\{f_X = 0\}$, de mesure nulle, sont arbitraires.

# Remarque
$Y \mid X$ représente la famille des lois conditionnelles $\mathbb{P}(Y \in \cdot \mid X = x)$ : ce n'est pas une loi unique, mais une famille de lois indexée par $x$. Dans le cas discret, elle est indexée par les valeurs $x$ telles que $p_X(x) > 0$ ; dans le cas continu, par presque tout $x$.

Dans le cas discret, $p_{Y|X}(y|x)$ n'est autre que la [[Probabilité conditionnelle|probabilité conditionnelle]] de $\{Y = y\}$ sachant $\{X = x\}$.

# Propriétés
**Indépendance**
- Pour tout couple $(x,y)$ tel que $p_X(x) > 0$ : $p_{Y|X}(y|x) = p_Y(y)$
- Pour presque tout couple $(x,y)$ tel que $f_X(x) > 0$ : $f_{Y|X}(y|x) = f_Y(y)$

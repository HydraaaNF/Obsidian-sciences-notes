# Définition
Soient $X$ et $Y$ deux variables aléatoires.

## Cas discret
$$p_{Y|X}(y|x) = \mathbb{P}(Y=y|X=x) = \frac{p_{X,Y}(x,y)}{p_X(x)} = \frac{p_{X,Y}(x,y)}{\sum_y p_{X,Y}(x,y)}$$
défini pour tout $x$ tel que $p_X(x) > 0$.

## Cas continu
$$f_{Y|X}(y|x) = \frac{f_{X,Y}(x,y)}{f_X(x)}$$
où $f_X(x) = \int_{-\infty}^{+\infty} f_{X,Y}(x,y)\,dy$ est la densité [[Lois marginales|marginale]] de $X$, défini pour tout $x$ tel que $f_X(x) > 0$.

# Remarque
$Y|X$ représente l'ensemble des distributions $\{Y|X=x,\ p_X(x)>0 \text{ ou } f_X(x)>0\}$ : ce n'est pas une loi unique, mais une famille de lois indexée par $x$.

# Propriétés
**Indépendance**
- Pour tout couple $(x,y)$ tel que $p_X(x) > 0$ : $p_{Y|X}(y|x) = p_Y(y)$
- Pour tout couple $(x,y)$ tel que $f_X(x) > 0$ : $f_{Y|X}(y|x) = f_Y(y)$

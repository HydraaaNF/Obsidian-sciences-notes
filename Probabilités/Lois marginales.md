# Définition

Soit $(X, Y)$ un [[Vecteur aléatoire|vecteur aléatoire]] de [[Loi d'un vecteur aléatoire|loi jointe]] $p_{X,Y}$ dans le cas discret, ou de densité jointe $f_{X,Y}$ dans le cas continu.

## Loi marginale

La **loi marginale** de $X$ est la loi de $X$ seule, déduite de la loi jointe du couple $(X, Y)$ :

- dans le cas discret, la probabilité marginale de $X$ vaut $\mathbb{P}(X = x) = \sum_y p_{X,Y}(x,y)$ ;
- dans le cas continu, la **densité marginale** de $X$ vaut $f_X(x) = \int_{-\infty}^{\infty} f_{X,Y}(x,y) dy$.

## Loi conditionnelle

La **loi conditionnelle** de $Y$ sachant $X = x$ s'appuie sur la [[Probabilité conditionnelle|probabilité conditionnelle]] et rapporte la loi jointe à la loi marginale de $X$.

Dans le cas discret :

$$p_{Y|X}(y|x) = \mathbb{P}(Y = y | X = x) = \frac{\mathbb{P}(Y = y, X = x)}{\mathbb{P}(X = x)} = \frac{p_{X,Y}(x,y)}{\sum_y p_{X,Y}(x,y)}$$

Dans le cas continu :

$$f_{Y|X}(y|x) = \frac{f_{X,Y}(x,y)}{f_X(x)}$$

$Y|X$ désigne l'ensemble des distributions $\{Y|X = x,\ p_X(x) > 0 \text{ ou } f_X(x) > 0\}$.

# Remarque

Lorsque $X$ et $Y$ sont [[Indépendance de variables aléatoires|indépendantes]], les lois conditionnelles coïncident avec les lois marginales. Pour l'indépendance des coordonnées d'un vecteur aléatoire, voir [[Indépendance des coordonnées d'un vecteur aléatoire]].

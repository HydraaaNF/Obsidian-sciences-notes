# Définition

Deux [[Variable aléatoire|variables aléatoires]] $X$ et $Y$ sont **indépendantes** lorsque la fonction de répartition de leur couple est le produit de leurs fonctions de répartition marginales :

$$F_{X,Y}(x,y) = F_X(x)F_Y(y)$$

pour tout couple $(x,y)$. Ici $F_{X,Y}$ désigne la [[Loi d'un vecteur aléatoire|fonction de répartition jointe]] du couple, et $F_X$, $F_Y$ les [[Fonction de répartition|fonctions de répartition]] de $X$ et de $Y$.

## Cas discret

Soient $(\Omega, \mathcal{F}, \mathbb{P})$ un espace probabilisé, $X$ et $Y$ deux variables aléatoires réelles discrètes définies sur $\Omega$. On dit que $X$ et $Y$ sont **indépendantes** lorsque

$$\forall j \in X(\Omega),\ \forall k \in Y(\Omega), \quad \mathbb{P}(X = j, Y = k) = \mathbb{P}(X = j)\mathbb{P}(Y = k).$$

Pour une suite finie ou infinie $(X_n)$ de variables aléatoires réelles, on dit qu'elles sont (mutuellement) indépendantes lorsque, pour toute suite $(k_n)$ avec $k_n \in X_n(\Omega)$, les évènements $[X_n = k_n]$ sont mutuellement indépendants.

# Propriétés

L'indépendance se lit également sur les lois conditionnelles : conditionner par $X = x$ ne modifie pas la loi de $Y$, la loi conditionnelle de $Y$ sachant $X = x$ coïncidant avec la [[Lois marginales|loi marginale]] de $Y$.

Dans le cas discret, pour tout couple $(x,y)$ tel que $p_X(x) > 0$ :

$$p_{Y|X}(y|x) = p_Y(y)$$

Dans le cas continu, pour tout couple $(x,y)$ tel que $f_X(x) > 0$ :

$$f_{Y|X}(y|x) = f_Y(y)$$

# Remarque

- L'indépendance de deux variables aléatoires prolonge l'[[Indépendance mutuelle d'évènements|indépendance des évènements]].
- Elle se généralise à un nombre quelconque de variables aléatoires : voir [[Indépendance des coordonnées d'un vecteur aléatoire]].
- Voir aussi l'[[Espérance d'un produit de variables aléatoires indépendantes]] et les [[Variables aléatoires non corrélées]].

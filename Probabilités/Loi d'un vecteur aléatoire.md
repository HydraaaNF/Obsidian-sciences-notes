# Définition

Soit $(X, Y)$ un [[Vecteur aléatoire|vecteur aléatoire]] de $\mathbb{R}^2$. La **loi jointe** (ou *distribution jointe*) de $X$ et de $Y$ est définie par sa [[Fonction de répartition|fonction de répartition]] jointe :

$$F_{X,Y}(x, y) = \mathbb{P}(X \le x \cap Y \le y)$$

# Propriétés

Si les deux variables sont [[Variable aléatoire continue|continues]], il existe souvent une fonction $f$ (la **densité jointe** du couple) telle que

$$F_{X,Y}(x, y) = \int_{-\infty}^{x} \int_{-\infty}^{y} f(u, v)\,du\,dv$$

et, si la dérivée partielle existe,

$$f_{X,Y}(x, y) = \frac{\partial^2 F_{X,Y}(x, y)}{\partial x \partial y}$$

# Remarque

Si $X$ et $Y$ sont [[Indépendance des coordonnées d'un vecteur aléatoire|indépendantes]], la loi jointe se factorise : $F_{X,Y}(x, y) = F_X(x) F_Y(y)$.

Pour les lois de $X$ et de $Y$ prises séparément, voir [[Lois marginales]].

# Définition

Le coefficient de corrélation des rangs de Kendall, noté $\tau_{XY}$, mesure si deux [[Variable aléatoire|variables aléatoires]] $X$ et $Y$ varient dans le même sens. C'est une mesure de la [[Corrélation de deux caractères|corrélation entre deux caractères]].

Pour toutes les paires d'observations $(x_i, y_i)$ et $(x_j, y_j)$, on compte $1$ si les deux variables sont rangées dans le même ordre (c'est-à-dire $x_i < x_j$ et $y_i < y_j$), et $-1$ sinon. En notant $S$ la somme de ces contributions sur toutes les paires,

$$S = \sum_{i<j} \operatorname{signe}\left((x_i - x_j)(y_i - y_j)\right)$$

le coefficient de corrélation des rangs de Kendall est

$$\tau_{XY} = \frac{2S}{n(n-1)}$$

où $n$ est le nombre d'observations.

# Interprétation

L'idée est de regarder le signe du produit $(X_1 - X_2)(Y_1 - Y_2)$ : le produit est positif lorsque les deux variables varient dans le même sens entre les deux observations comparées ; la paire compte alors pour $1$, sinon pour $-1$.

# Remarque

D'autres coefficients mesurent l'association entre deux caractères, notamment le [[Coefficient de corrélation des rangs de Spearman]].

# Définition

Soient $X$ et $Y$ deux [[Variable aléatoire|variables aléatoires]] discrètes. L'**entropie conditionnelle** de $X$ sachant $Y$ est la quantité

$$H(X|Y) = \sum_{i,j} \mathbb{P}(x_i, y_j) \log_b \frac{\mathbb{P}(y_j)}{\mathbb{P}(x_i, y_j)}$$

où $x_i$ parcourt les valeurs de $X$, $y_j$ celles de $Y$, la somme portant sur tous les couples de valeurs, et où $\log_b$ désigne le logarithme de base $b$, la même base que celle de l'[[Entropie d'une variable aléatoire discrète|entropie]] de $X$.

# Interprétation

L'entropie conditionnelle mesure l'incertitude qui subsiste sur $X$ lorsque $Y$ est connue : c'est la moyenne, pondérée par les probabilités $\mathbb{P}(y_j)$ des valeurs de $Y$, des entropies des [[Probabilité conditionnelle|lois conditionnelles]] de $X$ sachant $Y = y_j$.

Comme l'[[Espérance conditionnelle|espérance conditionnelle]], elle s'obtient en moyennant une quantité attachée à la loi conditionnelle sur la loi de la variable de conditionnement, ce qui en fait l'analogue informationnel de la formule de l'espérance totale.

# Propriétés

En remplaçant la probabilité jointe par le produit de la probabilité conditionnelle et de la probabilité de la condition, $\mathbb{P}(x_i, y_j) = \mathbb{P}(x_i|y_j)\,\mathbb{P}(y_j)$, la définition s'écrit aussi

$$H(X|Y) = -\sum_{i,j} \mathbb{P}(x_i, y_j) \log_b \mathbb{P}(x_i|y_j)$$

L'entropie conditionnelle se déduit de l'entropie du couple $(X, Y)$ et de celle de $Y$ :

$$H(X|Y) = H(X, Y) - H(Y)$$

Le conditionnement ne peut pas augmenter l'incertitude :

$$H(X|Y) \leq H(X)$$

avec égalité si et seulement si $X$ et $Y$ sont [[Indépendance de variables aléatoires|indépendantes]].

L'entropie conditionnelle est nulle si et seulement si $X$ est déterminée par $Y$ : connaître $Y$ ne laisse alors aucune incertitude sur $X$.

# Remarque

- L'entropie conditionnelle n'est pas symétrique : $H(X|Y)$ et $H(Y|X)$ diffèrent en général. Lorsque $X$ et $Y$ sont indépendantes, $H(X|Y) = H(X)$ et $H(Y|X) = H(Y)$, de sorte que les deux quantités ne coïncident que si $H(X) = H(Y)$.
- La base du logarithme fixe l'unité de l'information : $b = 2$ la compte en bits, $b = e$ en nats.

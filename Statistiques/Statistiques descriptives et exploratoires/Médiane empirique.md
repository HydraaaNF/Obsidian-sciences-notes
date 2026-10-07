# Définition

Dans le cas d'une [[Variable aléatoire continue|variable aléatoire continue]] $X$, on appelle **médiane** de $X$ la valeur $M(X)$ telle que

$$\mathbb{P}[\{X \leq M(X)\}] = \frac{1}{2}.$$

Pour estimer une médiane, si la loi mère n'est pas trop dissymétrique, on aura $\mathbb{E}[X] \simeq M(X)$, et on peut prendre la [[Moyenne empirique|moyenne empirique]] $\overline{X}$ comme [[Estimateur|estimateur]] de la médiane. Cependant, dans le cas général, il est plus naturel, compte-tenu de l'interprétation de la médiane, de prendre pour estimation de $M(X)$ la [[Moyenne, médiane et mode|valeur médiane]] des observations $x_1, \dots, x_n$ : c'est la **médiane empirique**, qui partage la série triée en deux moitiés.

# Remarque

Attention, il ne faut pas confondre la médiane $M(X)$ et l'[[Espérance d'une variable aléatoire|espérance]] $\mathbb{E}[X]$ :

- Ces deux quantités sont généralement différentes lorsque la [[Probabilité à densité|densité]] est dissymétrique. Par exemple, pour une [[Loi exponentielle|loi exponentielle]] de paramètre $\lambda$, l'espérance vaut $1/\lambda$ et la médiane $\ln(2)/\lambda$.
- Par ailleurs, si toutes les lois continues admettent une médiane, certaines n'ont pas de [[Moment d'ordre k|moment d'ordre 1]] (par exemple, la [[Loi de Cauchy|loi de Cauchy]], dont la médiane est nulle).

Pour une loi mère ayant une densité continue et symétrique (paire) et admettant un moment d'ordre 1, l'espérance et la médiane sont égales. Par conséquent, on pourrait considérer la valeur médiane comme estimateur de $\mathbb{E}[X]$.

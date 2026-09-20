# Définition
Soient $X$ et $Y$ deux variables aléatoires.

$$\mathbb{E}[X|Y=y] = \sum_x x\, p_{X|Y}(x|y), \quad \text{quand } p_Y(y) > 0$$
$$\mathbb{E}[X|Y=y] = \int_{-\infty}^{+\infty} x\, f_{X|Y}(x|y)\,dx, \quad \text{quand } f_Y(y) > 0$$

où $p_{X|Y}$ et $f_{X|Y}$ sont données par la [[Loi conditionnelle d'une variable aléatoire]].

# Remarque
$\mathbb{E}[X|Y=y]$ est une fonction de $y$ (et non une variable aléatoire en soi tant que $y$ n'est pas remplacé par $Y$).

# Propriétés
**Formule de la moyenne totale (tour)**
$$\mathbb{E}[X] = \sum_y \mathbb{E}[X|Y=y]\, p_Y(y) = \mathbb{E}_Y\big[\mathbb{E}[X|Y]\big]$$

**Indépendance** : si $X$ et $Y$ sont indépendantes,
$$\mathbb{E}[X|Y=y] = \mathbb{E}[X]$$

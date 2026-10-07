# Définition

La **fonction de répartition** (en anglais *cumulative distribution function*, cdf) d'une [[Variable aléatoire|variable aléatoire]] réelle $X$ est la fonction $F_X$ définie par

$$\forall t \in \mathbb{R}, \quad F_X(t) = \mathbb{P}(X \leq t).$$

C'est la probabilité que $X$ prenne une valeur inférieure ou égale à $t$. Pour une [[Variable aléatoire continue|variable aléatoire continue]] de [[Probabilité à densité|densité de probabilité]] $f_X$,

$$F_X(t) = \int_{-\infty}^{t} f_X(x)\,dx.$$

# Propriétés

La probabilité qu'une variable aléatoire continue de densité $f_X$ prenne une valeur dans un intervalle s'exprime à l'aide de la fonction de répartition :

$$\mathbb{P}(a < X < b) = \int_a^b f_X(x)\,dx = F_X(b) - F_X(a).$$

La densité est la dérivée de la fonction de répartition :

$$f_X(x) = \lim_{\delta \to 0^+} \frac{\mathbb{P}(x < X < x + \delta)}{\delta} = F_X'(x).$$

Soit $X$ une variable aléatoire réelle, alors :

- $F_X$ est croissante sur $\mathbb{R}$ ;
- $\lim_{t \to -\infty} F_X(t) = 0$ et $\lim_{t \to +\infty} F_X(t) = 1$ ;
- pour tout réel $t$, $F_X(t^-) = \mathbb{P}(X < t)$ et $F_X(t^+) = \mathbb{P}(X \leq t)$ ;
- $F_X$ est continue à droite sur $\mathbb{R}$ ;
- pour tout réel $t$, le saut de $F_X$ en $t$ vaut $\mathbb{P}(X = t)$ ;
- si $X$ est discrète, $F_X$ est une fonction en escalier et ses points de discontinuité forment l'ensemble $X(\Omega)$ des valeurs prises par $X$ ;
- si $X$ est continue, $F_X$ est continue sur $\mathbb{R}$ ; si de plus sa densité $f_X$ est continue par morceaux, $F_X$ est dérivable en tout point de continuité de $f_X$ et $F_X'(t) = f_X(t)$ en un tel point.

Réciproquement, soit $F$ une fonction croissante sur $\mathbb{R}$, continue à droite, vérifiant $\lim_{t \to -\infty} F(t) = 0$ et $\lim_{t \to +\infty} F(t) = 1$. Il existe un espace probabilisé $(\Omega, \mathcal{F}, \mathbb{P})$ et une variable aléatoire réelle $X$ tels que $F_X = F$.

# Exemple

Pour une [[Variable aléatoire discrète|variable aléatoire discrète]] prenant les valeurs $0$, $1$, $2$ et $3$, la fonction de répartition est une fonction en escalier : constante entre deux valeurs prises par la variable, elle saute en chacune d'elles.

| $x$ | 0 | 1 | 2 | 3 |
|---|---|---|---|---|
| $F(x)$ | 0.125 | 0.5 | 0.875 | 1 |

Les valeurs du tableau sont approchées.

# Remarque

- La fonction de répartition détermine entièrement la [[Loi d'une variable aléatoire|loi]] de la variable : deux variables aléatoires ont même loi si et seulement si elles ont même fonction de répartition. Voir [[Caractérisation de la loi par la fonction de répartition]].
- L'écriture $f(x) = \lim_{\delta \to 0^+} \mathbb{P}(x < X < x + \delta)$ est une erreur fréquente : elle omet la division par $\delta$. La probabilité $\mathbb{P}(x < X < x + \delta)$ tend vers $0$ avec $\delta$ ; c'est son taux d'accroissement, $\frac{\mathbb{P}(x < X < x + \delta)}{\delta}$, qui converge vers la densité $f(x) = F'(x)$.

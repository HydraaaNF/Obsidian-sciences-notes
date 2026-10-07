# Interprétation

Un [[Estimateur|estimateur]] biaisé n'est pas nécessairement un mauvais estimateur : le biais n'est qu'une composante de l'[[Erreur quadratique moyenne|erreur quadratique moyenne]], et un estimateur biaisé peut être préféré à un estimateur sans biais dont la variance est plus grande.

# Exemple

## Estimateurs de la variance à moyenne connue

En supposant la moyenne $m$ connue, considérons les estimateurs de la [[Variance|variance]] suivants, l'un biaisé et l'autre sans biais :

$$T = \frac{1}{n} \sum (X_i - m)^2$$

$$S_0^2 = \frac{1}{n-1} \sum (X_i - m)^2$$

On peut montrer que $T$ est meilleur que $S_0^2$ puisque $\mathbb{V}[T] < \mathbb{V}[S_0^2]$.

## Estimateurs de l'autocorrélation à moyenne connue et nulle

En supposant la moyenne $m$ connue et nulle, considérons les estimateurs suivants de l'autocorrélation $r(p) = \mathbb{E}[X_i X_{i-p}]$, l'un biaisé et l'autre sans biais :

$$R_0 = \frac{1}{n-p} \sum_{i=1}^{n-p} X_i X_{i+p}$$

$$R_1 = \frac{1}{n} \sum_{i=1}^{n-p} X_i X_{i+p}$$

$R_0$ est sans biais mais de variance énorme lorsque $p \to n$ ; dans ce cas, $R_1$ est souvent préféré.

# Remarque

Les estimateurs de la variance ci-dessus supposent la moyenne $m$ connue ; lorsque la moyenne est inconnue, voir la [[Variance empirique|variance empirique]]. Restreindre la recherche du meilleur estimateur aux estimateurs sans biais conduit à la notion d'[[Estimateur sans biais de variance minimale]].

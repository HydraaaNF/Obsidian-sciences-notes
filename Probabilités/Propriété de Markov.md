# Définition

Un [[Processus stochastique|processus stochastique]] $\{X(t) \mid t \in T\}$ est un **processus de Markov** si, pour tout $t_0 < t_1 < \ldots < t_n < t$, la distribution conditionnelle de $X(t)$ sachant $X(t_0), \ldots, X(t_n)$ ne dépend que de $X(t_n)$, c'est-à-dire :

$$\mathbb{P}[X(t) \leq x \mid X(t_n) \leq x_n, \ldots, X(t_0) \leq x_0] = \mathbb{P}[X(t) \leq x \mid X(t_n) \leq x_n]$$

# Propriétés

Une [[Chaîne de Markov à temps discret|chaîne de Markov]] est dite **homogène** si

$$\mathbb{P}[X(t) \leq x \mid X(t_n) \leq x_n] = \mathbb{P}[X(t - t_n) \leq x \mid X(0) \leq x_n]$$

# Remarque

La condition portant sur l'instant $t_0$ s'écrit $X(t_0) \leq x_0$ : écrire $X(t_0) \leq t_0$ (comparer la valeur du processus à un instant, et non à une valeur $x_0$ comme dans les autres conditions) est une erreur fréquente.

La propriété de Markov est la forme générale de la propriété qui définit la [[Chaîne de Markov à temps continu]] et la [[Chaîne de Markov à temps discret]] ; elle se généralise à la [[Chaîne de Markov d'ordre N]] et, pour des indices spatiaux, au [[Champ aléatoire de Markov]]. Le [[Processus de Poisson]] en est un exemple à temps continu.

# Définition

Soit $(X_n)_{n \in \mathbb{N}}$ une suite de [[Variable aléatoire réelle|v.a.r.]] et $X$ une v.a.r. définies sur un même [[Espace probabilisé|espace probabilisé]]. On dit que la suite $(X_n)_{n \in \mathbb{N}}$ converge en probabilité vers $X$ si

$$\forall \eta > 0, \mathbb{P}[|X_n - X| > \eta] \xrightarrow{n \to +\infty} 0$$

On note alors $X_n \xrightarrow{\mathbb{P}} X$.

# Interprétation

Cela signifie que la probabilité que $X_n$ s'écarte de $X$ de plus de $\eta$ tend vers 0 quand $n$ tend vers l'infini, aussi petit que soit $\eta$.

# Exemple

On considère la suite de [[Variable aléatoire réelle|v.a.r.]] $(X_n)_{n \in \mathbb{N}^*}$ où pour tout $n \in \mathbb{N}^*$

$$\mathbb{P}[X_n = a_n] = p_n$$

$$\mathbb{P}[X_n = 0] = 1 - p_n.$$

1. Si $\lim_{n \to +\infty} p_n = 0$ : soit $\eta > 0$,

$$\begin{aligned}\mathbb{P}[|X_n| > \eta] &\leq \mathbb{P}[X_n = a_n] \\ &\leq p_n \\ &\xrightarrow{n \to +\infty} 0\end{aligned}$$

On en déduit que $X_n \xrightarrow{\mathbb{P}} 0$.

2. Si $\lim_{n \to +\infty} a_n = 0$ : soit $\eta > 0$, il existe $N \in \mathbb{N}$ tel que pour tout $n \geq N$ on a $|a_n| \leq \eta$. Ainsi, pour tout $n \geq N$,

$$\mathbb{P}[|X_n| > \eta] = 0.$$

et on en déduit de nouveau que $X_n \xrightarrow{\mathbb{P}} 0$.

# Remarque

En règle générale, pour montrer qu'une suite $(X_n)_{n \in \mathbb{N}}$ converge en probabilité vers $X$, il peut être nécessaire de connaître la loi conjointe de $(X_n, X)$. Le calcul ou la simple majoration de $\mathbb{P}[|X_n - X| > \eta]$ sont facilités lorsque $X$ est constante.

La [[Convergence presque sûre]] est une propriété plus forte que la convergence en probabilité. La convergence en probabilité est l'un des modes de convergence stochastique d'une suite de variables aléatoires ; voir aussi la [[Convergence en loi]] et la [[Convergence en moyenne d'ordre p]].

# Définition

Soit $p \geq 1$. Soit $(X_n)$ une suite de [[Variable aléatoire réelle|variables aléatoires réelles]] et $X$ une variable aléatoire réelle, toutes définies sur le même [[Espace probabilisé|espace probabilisé]]. On suppose que ces variables aléatoires admettent toutes un [[Moment d'ordre k|moment]] d'ordre $p$. On dit que la suite $(X_n)$ converge en moyenne d'ordre $p$ vers $X$ si

$$\lim_{n \to +\infty} \mathbb{E}\left(|X_n - X|^p\right) = 0$$

où $\mathbb{E}$ désigne l'[[Espérance d'une variable aléatoire|espérance]]. On note alors $X_n \xrightarrow{\mathbb{L}^p} X$.

Pour $p = 1$ on parle de convergence en moyenne, et pour $p = 2$ de convergence en moyenne quadratique.

# Propriétés

Soit $p > q \geq 1$. Sous les hypothèses de la définition précédente, si $X_n \xrightarrow{\mathbb{L}^p} X$ alors $X_n \xrightarrow{\mathbb{L}^q} X$.

# Théorème

Soit $p \geq 1$. Si la suite $(X_n)$ converge en moyenne d'ordre $p$ vers $X$, alors elle [[Convergence en probabilité|converge en probabilité]] vers $X$.

# Remarque

La convergence en moyenne d'ordre $p$ est l'un des modes de convergence stochastique d'une suite de variables aléatoires (il en existe d'autres).

La réciproque est fausse en général : la convergence en probabilité n'entraîne pas la convergence en moyenne d'ordre $p$.

# Exemple

On considère la suite $(X_n)_{n \in \mathbb{N}^*}$ où, pour tout $n \in \mathbb{N}^*$, $X_n(\Omega) = \{-n, 0, n\}$ et

$$\mathbb{P}[X_n = -n] = \mathbb{P}[X_n = n] = \frac{1}{n^2}.$$

Cette suite [[Convergence en probabilité|converge en probabilité]] vers $0$. Ainsi, si la suite converge en moyenne d'ordre $p$ vers une limite, celle-ci est également $0$.

- Pour $p = 2$, on a $\mathbb{E}\left[|X_n|^2\right] = 2$ : la suite ne converge pas en moyenne quadratique vers $0$.
- Pour $p = 1$, on a $\mathbb{E}\left[|X_n|\right] = \frac{2}{n} \xrightarrow{n \to +\infty} 0$ : la suite converge donc en moyenne vers $0$, ce qui implique la convergence en probabilité.

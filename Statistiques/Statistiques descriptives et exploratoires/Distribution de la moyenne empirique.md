# Propriétés

Soit $X_1, \ldots, X_n$ un [[Échantillon et échantillonnage|échantillon]] de variables aléatoires [[Indépendance de variables aléatoires|indépendantes]] et identiquement distribuées, d'[[Espérance d'une variable aléatoire|espérance]] $m$ et de [[Variance|variance]] $\sigma^2$, et soit $\overline{X}$ la [[Moyenne empirique|moyenne empirique]] associée.

L'[[Espérance d'une variable aléatoire|espérance]] et la [[Variance|variance]] de $\overline{X}$ valent

$$\mathbb{E}[\overline{X}] = m$$

$$\mathbb{V}[\overline{X}] = \frac{\sigma^2}{n}$$

L'[[Estimateur|estimateur]] $\overline{X}$ [[Convergence en moyenne d'ordre p|converge en moyenne quadratique]] vers $m$ quand $n \to \infty$, puisque $\mathbb{E}\left[(\overline{X} - m)^2\right] \to 0$.

# Théorème

D'après le [[Théorème de la limite centrale]], la variable centrée réduite construite à partir de la moyenne empirique [[Convergence en loi|converge en loi]] vers la [[Loi gaussienne|loi gaussienne centrée réduite]] :

$$\frac{\overline{X} - m}{\sigma/\sqrt{n}} \xrightarrow{\mathcal{L}} \mathcal{N}(0, 1)$$

# Remarque

**Note sur les variables gaussiennes** : pour des variables gaussiennes, la convergence est en fait une égalité, c'est-à-dire que si $X \sim \mathcal{N}(0, 1)$, alors $\overline{X} \sim \mathcal{N}\left(m, \frac{\sigma}{\sqrt{n}}\right)$.

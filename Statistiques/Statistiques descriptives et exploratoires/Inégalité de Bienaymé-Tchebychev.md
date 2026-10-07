# Théorème

Soit $X$ une [[Variable aléatoire réelle|v.a.r.]] de carré intégrable. Alors

$$\forall \varepsilon > 0 \quad \mathbb{P}\left(|X - \mathbb{E}(X)| \geq \varepsilon\right) \leq \frac{\mathbb{V}(X)}{\varepsilon^{2}}$$

### Démonstration

Soit $X$ une v.a.r. de carré intégrable, on pose $Y = |X - \mathbb{E}(X)|^{2}$. La v.a.r. $Y$ est positive et intégrable. Ainsi, d'après l'[[Inégalité de Markov]] appliquée à $Y$ avec $\lambda = \varepsilon^{2}$, on a pour tout $\varepsilon > 0$

$$\mathbb{P}\left(|X - \mathbb{E}(X)| \geq \varepsilon\right) = \mathbb{P}\left(Y \geq \varepsilon^{2}\right) \leq \frac{\mathbb{E}(Y)}{\varepsilon^{2}} = \frac{\mathbb{V}(X)}{\varepsilon^{2}}.$$

# Remarque

L'inégalité de Bienaymé-Tchebychev est un cas particulier de l'[[Inégalité de Markov]] : elle s'obtient en appliquant cette dernière à la variable aléatoire positive $Y = |X - \mathbb{E}(X)|^{2}$, avec $\lambda = \varepsilon^{2}$. Elle majore la probabilité que $X$ s'écarte de son [[Espérance d'une variable aléatoire|espérance]] d'au moins $\varepsilon$, à l'aide de sa [[Variance]].

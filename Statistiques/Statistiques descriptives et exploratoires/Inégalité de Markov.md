# Théorème

Soit $X$ une [[Variable aléatoire réelle|variable aléatoire réelle]] positive et intégrable. Alors

$$\forall \lambda > 0 \quad \mathbb{P}(X \geq \lambda) \leq \frac{\mathbb{E}(X)}{\lambda}$$

### Démonstration

Soit $\lambda > 0$ et $X$ une variable aléatoire réelle positive et intégrable. On a

$$\begin{aligned}
\mathbb{P}(X \geq \lambda) &= \mathbb{E}\left[\mathbf{1}_{\{\omega \in \Omega \mid X(\omega) \geq \lambda\}}\right] \\
&= \int_{\Omega} \mathbf{1}_{\{\omega \in \Omega \mid X(\omega) \geq \lambda\}}(u) \, d\mathbb{P}(u)
\end{aligned}$$

On peut remarquer que pour tout $u \in \Omega$,

$$\mathbf{1}_{\{\omega \in \Omega \mid X(\omega) \geq \lambda\}}(u) \leq \frac{X(u)}{\lambda}$$

car $X$ et $\lambda$ sont positives. Ainsi,

$$\begin{aligned}
\mathbb{P}(X \geq \lambda) &\leq \int_{\Omega} \frac{X(u)}{\lambda} \, d\mathbb{P}(u) \\
&\leq \frac{\mathbb{E}(X)}{\lambda}
\end{aligned}$$

# Remarque

L'inégalité de Markov majore la probabilité que $X$ soit au moins égale à $\lambda$ par l'[[Espérance d'une variable aléatoire|espérance]] de $X$ divisée par $\lambda$.

L'[[Inégalité de Bienaymé-Tchebychev]] s'en déduit en appliquant l'inégalité de Markov à la variable aléatoire $Y = |X - \mathbb{E}(X)|^2$, positive et intégrable dès que $X$ est de carré intégrable, avec $\lambda = \varepsilon^2$ : on obtient

$$\forall \varepsilon > 0 \quad \mathbb{P}(|X - \mathbb{E}(X)| \geq \varepsilon) \leq \frac{\mathbb{V}(X)}{\varepsilon^2}$$

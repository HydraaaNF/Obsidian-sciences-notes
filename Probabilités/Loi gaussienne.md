# Loi

La loi gaussienne, ou loi normale, est une [[Probabilité à densité|loi à densité]] de moyenne $\mu$ et d'écart-type $\sigma$. Pour une [[Variable aléatoire continue|variable aléatoire continue]] $X$, la densité s'écrit

$$f(x) = \frac{1}{\sqrt{2\pi}\sigma} \exp\left\{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2\right\}.$$

Son [[Espérance d'une variable aléatoire|espérance]] vaut $\mathbb{E}[X] = \mu$ et sa [[Variance|variance]] $\mathbb{V}[X] = \sigma^2$.

# Propriétés

**Changement de variable.** Si $X$ suit la loi $\mathcal{N}(\mu, \sigma^2)$, alors

$$U = (X - \mu)/\sigma \sim \mathcal{N}(0, 1).$$

**Fonction caractéristique.** Si $X$ suit la loi $\mathcal{N}(\mu, \sigma^2)$, alors

$$\Phi_X(\xi) = e^{i\mu\xi - \frac{\sigma^2\xi^2}{2}}.$$

**Additivité.** Si $X_1$ et $X_2$ sont deux variables aléatoires [[Indépendance de variables aléatoires|indépendantes]], de lois respectives $\mathcal{N}(\mu_1, \sigma_1^2)$ et $\mathcal{N}(\mu_2, \sigma_2^2)$, alors

$$X_1 + X_2 \sim \mathcal{N}(\mu_1 + \mu_2, \sigma_1^2 + \sigma_2^2).$$

**Intervalles centrés.** Les probabilités que $X$ appartienne à un intervalle centré sur sa moyenne $m$ valent :

- $\mathbb{P}[m - 1.64\sigma < X < m + 1.64\sigma] = 0.90$ ;
- $\mathbb{P}[m - 1.96\sigma < X < m + 1.96\sigma] = 0.95$ ;
- $\mathbb{P}[m - 3.09\sigma < X < m + 3.09\sigma] = 0.998$.

**Kurtosis.** Le kurtosis de la loi gaussienne vaut $\gamma_2 = 3$ (voir [[Asymétrie et aplatissement|asymétrie et aplatissement]]).

# Interprétation

La densité a la forme d'une cloche symétrique, maximale en $x = \mu$ et décroissante quand on s'en éloigne. Plus l'écart-type $\sigma$ est petit, plus la cloche est haute et resserrée autour de $\mu$ ; plus $\sigma$ est grand, plus elle est aplatie et étalée.

La loi gaussienne est la plus utilisée des lois continues : elle s'applique à presque toutes les situations.

Pour $\mu = 0$, densités pour trois écart-types (valeurs calculées à partir de la formule ci-dessus, arrondies à $10^{-4}$) :

```chart
type: line
labels: ["-6", "-5.5", "-5", "-4.5", "-4", "-3.5", "-3", "-2.5", "-2", "-1.5", "-1", "-0.5", "0", "0.5", "1", "1.5", "2", "2.5", "3", "3.5", "4", "4.5", "5", "5.5", "6"]
series:
  - title: σ = 1
    data: [0.0, 0.0, 0.0, 0.0, 0.0001, 0.0009, 0.0044, 0.0175, 0.054, 0.1295, 0.242, 0.3521, 0.3989, 0.3521, 0.242, 0.1295, 0.054, 0.0175, 0.0044, 0.0009, 0.0001, 0.0, 0.0, 0.0, 0.0]
  - title: σ = 2
    data: [0.0022, 0.0045, 0.0088, 0.0159, 0.027, 0.0431, 0.0648, 0.0913, 0.121, 0.1506, 0.176, 0.1933, 0.1995, 0.1933, 0.176, 0.1506, 0.121, 0.0913, 0.0648, 0.0431, 0.027, 0.0159, 0.0088, 0.0045, 0.0022]
  - title: σ = 3
    data: [0.018, 0.0248, 0.0332, 0.0432, 0.0547, 0.0673, 0.0807, 0.094, 0.1065, 0.1174, 0.1258, 0.1311, 0.133, 0.1311, 0.1258, 0.1174, 0.1065, 0.094, 0.0807, 0.0673, 0.0547, 0.0432, 0.0332, 0.0248, 0.018]
```

# Exemple

Des mesures d'énergie se répartissent en deux populations qui se recouvrent : une population de basse énergie et une population de haute énergie, modélisées chacune par une loi gaussienne. Pour les séparer, on place un seuil de décision à

$$m_1 - a\,s_1$$

où $m_1$ et $s_1$ sont la moyenne et l'écart-type de la population de haute énergie, et $a$ un coefficient.

# Remarque

La propriété d'additivité de la loi gaussienne ne s'applique que si les variables sont indépendantes.

# Liens avec d'autres lois

- La loi gaussienne est le cas particulier de dimension 1 du [[Vecteur gaussien|vecteur gaussien]].
- Elle est la loi limite du [[Théorème de la limite centrale|théorème de la limite centrale]].
- Toute combinaison linéaire de variables aléatoires gaussiennes [[Indépendance de variables aléatoires|indépendantes]] est gaussienne : si $X \sim \mathcal{N}(\mu_1, \sigma_1^2)$ et $Y \sim \mathcal{N}(\mu_2, \sigma_2^2)$, alors $aX + bY \sim \mathcal{N}(a\mu_1 + b\mu_2, a^2\sigma_1^2 + b^2\sigma_2^2)$.
- Le carré d'une variable aléatoire de loi normale centrée réduite suit la [[Loi du chi-deux|loi du chi-deux]] à un degré de liberté : si $X \sim \mathcal{N}(0, 1)$, alors $X^2 \sim \chi_1^2$.
- Le quotient de deux variables aléatoires indépendantes de loi normale centrée réduite suit la [[Loi de Cauchy|loi de Cauchy]] de paramètres $m = 0$ et $a = 1$.
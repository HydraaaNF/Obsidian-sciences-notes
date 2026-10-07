# Définition

Soit $X_1, \ldots, X_n$ un [[Échantillon et échantillonnage|échantillon]] de variables aléatoires [[Indépendance de variables aléatoires|indépendantes]] et identiquement distribuées, de loi normale de moyenne $m$ inconnue et de variance $\sigma^2$ connue. La [[Moyenne empirique|moyenne empirique]]

$$\overline{X} = \frac{1}{n} \sum_{i=1}^{n} X_i$$

est une [[Loi gaussienne|variable aléatoire gaussienne]] de moyenne $m$ et d'écart-type $\frac{\sigma}{\sqrt{n}}$ (voir [[Distribution de la moyenne empirique]]) :

$$\overline{X} \to \mathcal{N}\left(m\,;\, \frac{\sigma}{\sqrt{n}}\right)$$

Pour une variable $U$ de [[Quantile de la loi normale centrée réduite|loi normale centrée réduite]], $\mathbb{P}(-1{,}64 < U < 1{,}64) = 0{,}9$. On en déduit qu'avec une probabilité de $0{,}9$ (9 chances sur 10),

$$m - 1{,}64\,\frac{\sigma}{\sqrt{n}} < \overline{X} < m + 1{,}64\,\frac{\sigma}{\sqrt{n}},$$

ce qui définit l'[[Intervalle de confiance|intervalle de confiance]] de niveau $0{,}9$ de la moyenne :

$$\left[\overline{X} - 1{,}64\,\frac{\sigma}{\sqrt{n}}\,;\ \overline{X} + 1{,}64\,\frac{\sigma}{\sqrt{n}}\right]$$

# Exemple

Une ligne de production fabrique des objets d'une longueur donnée ; une étude antérieure a établi que la distribution réelle de la longueur est une loi normale de moyenne $10$ et d'écart-type $2$. Pour le contrôle qualité, un échantillon de $25$ objets est prélevé. Quelle est la plage de valeurs dans laquelle la moyenne empirique $\overline{X}$ a 9 chances sur 10 de se trouver ?

La loi de la moyenne empirique donne ici

$$\overline{X} \to \mathcal{N}\left(10\,;\, \frac{2}{\sqrt{25}}\right)$$

Comme, pour une variable $U$ de loi normale centrée réduite, $\mathbb{P}(-1{,}64 < U < 1{,}64) = 0{,}9$, on a, avec une probabilité de $0{,}9$ :

$$10 - 1{,}64\,\frac{2}{\sqrt{25}} < \overline{X} < 10 + 1{,}64\,\frac{2}{\sqrt{25}}$$

La plage de valeurs de $\overline{X}$ est $[9{,}34\,;\ 10{,}66]$.

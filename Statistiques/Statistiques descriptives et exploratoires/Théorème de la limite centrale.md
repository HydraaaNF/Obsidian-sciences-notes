# Théorème

Soit $(X_n)_{n \in \mathbb{N}^*}$ une suite de [[Variable aléatoire réelle|variables aléatoires réelles]] indépendantes et identiquement distribuées (i.i.d.) admettant un moment d'ordre 2. Alors la [[Moyenne empirique|moyenne empirique]] $\overline{X}$ vérifie

$$\frac{\overline{X} - \mathbb{E}[\overline{X}]}{\sqrt{\mathbb{V}(\overline{X})}} = \frac{\overline{X} - m}{\sqrt{\frac{\sigma^2}{n}}} \xrightarrow[n \to +\infty]{\mathcal{L}} \mathcal{N}(0,1)$$

où $m = \mathbb{E}[X_1]$ et $\sigma^2 = \mathbb{V}(X_1)$ : la variable centrée réduite $\frac{\overline{X} - m}{\sqrt{\frac{\sigma^2}{n}}}$ [[Convergence en loi|converge en loi]] vers la [[Loi gaussienne|loi gaussienne centrée réduite]] $\mathcal{N}(0,1)$.

### Démonstration

Pour tout $n \in \mathbb{N}^*$, on définit $Y_n = \frac{X_n-m}{\sigma}$. On a donc $\mathbb{E}[Y_n] = 0$ et $\mathbb{V}(Y_n) = \mathbb{E}[Y_n^2] = 1$. Par ailleurs, $(X_n)_{n\in\mathbb{N}^{*}}$ étant une suite de variables aléatoires i.i.d., la suite $(Y_n)_{n\in\mathbb{N}^{*}}$ l'est également. On pose

$$\begin{aligned} Z_n &= \frac{\overline{X} - m}{\sqrt{\frac{\sigma^2}{n}}} \\ &= \frac{1}{n} \times \frac{\sum_{k=1}^n X_k - nm}{\sqrt{\frac{\sigma^2}{n}}} \\ &= \frac{1}{\sqrt{n}} \times \frac{\sum_{k=1}^n (X_k - m)}{\sigma} \\ &= \frac{1}{\sqrt{n}} \sum_{k=1}^n Y_k \end{aligned}$$

Calculons la [[Fonction caractéristique|fonction caractéristique]] de $Z_n$ : soit $t \in \mathbb{R}$,

$$\begin{aligned}\Phi_{Z_n}(t) &= \mathbb{E} \left[ e^{itZ_n} \right] \\ &= \mathbb{E} \left[ e^{i \frac{t}{\sqrt{n}} \sum_{k=1}^n Y_k} \right] \\ &= \mathbb{E} \left[ \prod_{k=1}^n e^{i \frac{t}{\sqrt{n}} Y_k} \right] \\ &= \prod_{k=1}^n \mathbb{E} \left[ e^{i \frac{t}{\sqrt{n}} Y_k} \right] \quad \text{par indépendance des } Y_k \\ &= \left( \mathbb{E} \left[ e^{i \frac{t}{\sqrt{n}} Y_1} \right] \right)^n \quad \text{car les } Y_k \text{ sont identiquement distribuées}\end{aligned}$$

Pour $n$ au voisinage de $+\infty$, la variable aléatoire $U = i \frac{t}{\sqrt{n}} Y_1$ prend ses valeurs au voisinage de $0$. On effectue donc un développement limité de $e^U$ :

$$\begin{aligned}
\Phi_{Z_n}(t)
&= \left( \mathbb{E}\left[1+i\frac{t}{\sqrt{n}}Y_1-\frac{t^2}{2n}Y_1^2+\underset{n\to+\infty}{o}\left(\frac{1}{n}\right)\right]\right)^n \\
&= \left(1+i\frac{t}{\sqrt{n}}\mathbb{E}[Y_1]-\frac{t^2}{2n}\mathbb{E}[Y_1^2]+\underset{n\to+\infty}{o}\left(\frac{1}{n}\right)\right)^n \\
&= \left(1-\frac{t^2}{2n}+\underset{n\to+\infty}{o}\left(\frac{1}{n}\right)\right)^n \\
&= e^{n\ln\left(1-\frac{t^2}{2n}+\underset{n\to+\infty}{o}\left(\frac{1}{n}\right)\right)} \\
&= e^{n\left(-\frac{t^2}{2n}+\underset{n\to+\infty}{o}\left(\frac{1}{n}\right)\right)} \\
&= e^{-\frac{t^2}{2}+\underset{n\to+\infty}{o}(1)} \\
&\xrightarrow{n\to+\infty} e^{-\frac{t^2}{2}}
\end{aligned}$$

On reconnaît la fonction caractéristique de la loi $\mathcal{N}(0,1)$. Ainsi, on conclut que la suite $(Z_n)_{n\in\mathbb{N}^*}$ converge en loi vers la loi $\mathcal{N}(0,1)$.

# Interprétation

Le théorème de la limite centrale, également appelé théorème « Central Limit », implique que, pour toute suite $(X_n)$ de variables aléatoires i.i.d. admettant un moment d'ordre 2, la loi de $\overline{X}$ peut être approchée pour $n$ grand par une [[Loi gaussienne|loi normale]] de paramètres l'[[Espérance d'une variable aléatoire|espérance]] $\mathbb{E}[\overline{X}]$ et la [[Variance|variance]] $\mathbb{V}(\overline{X})$, c'est-à-dire $\mathcal{N}\left(m,\frac{\sigma^2}{n}\right)$. On écrit encore « $\overline{X}$ suit approximativement une loi $\mathcal{N}\left(m,\frac{\sigma^2}{n}\right)$ ».

Ainsi, plus $n$ est grand, plus la densité de $\overline{X}$ est une gaussienne très localisée autour de $m$, l'écart-type $\frac{\sigma}{\sqrt{n}}$ devenant très petit.

# Remarque

Il est remarquable que ce résultat soit valable pour tout type de loi, que $X_n$ soit continue, discrète ou autre : c'est en ce sens que la loi normale joue un rôle central en probabilités et en statistiques.

Pour une loi quelconque et un échantillon de grande taille (en pratique $n \geq 100$ suffit dans la majorité des cas), le théorème de la limite centrale permet d'approcher la loi de $\overline{X}$ par une loi normale et de construire un [[Intervalle de confiance de la moyenne d'une loi quelconque|intervalle de confiance de la moyenne]] au niveau $1-\alpha$.

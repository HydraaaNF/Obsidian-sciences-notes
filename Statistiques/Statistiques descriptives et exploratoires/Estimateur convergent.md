# Définition

Un [[Estimateur|estimateur]] $T_n$ de $\theta$ est dit **convergent** (ou **faiblement consistant**) si

$$T_n \xrightarrow{\mathbb{P}} \theta$$

où le symbole $\xrightarrow{\mathbb{P}}$ signifie la [[Convergence en probabilité|convergence en probabilité]].

# Interprétation

Le minimum à exiger d'un estimateur est que si le nombre des observations croît, l'estimation $T_n(\omega)$ de $\theta$ se rapproche de la vraie valeur de $\theta$, c'est-à-dire

$$\lim_{n \rightarrow \infty} T_n(\omega) = \lim_{n \rightarrow \infty} f(X_1(\omega), \dots, X_n(\omega)) = \theta.$$

# Remarque

On rappelle schématiquement les implications entre les différents types de convergence classiques :

$$\begin{array}{c} \left(\xrightarrow{L^p}\right) \\[6pt] \Downarrow \\[6pt] \left(\xrightarrow{\text{p.s.}}\right) \;\implies\; \left(\xrightarrow{\mathbb{P}}\right) \;\implies\; \left(\xrightarrow{\mathcal{L}}\right) \end{array}$$

Autrement dit, la [[Convergence en moyenne d'ordre p|convergence en moyenne d'ordre $p$]] implique la convergence en probabilité, la [[Convergence presque sûre|convergence presque sûre]] implique la convergence en probabilité, et la convergence en probabilité implique la [[Convergence en loi|convergence en loi]]. Un [[Estimateur fortement convergent|estimateur fortement convergent]] est donc convergent.

# Exemple

**Lancer d'une pièce truquée.** On considère une pièce truquée et on souhaite estimer la probabilité d'obtenir la face pile. Cela revient à considérer comme loi mère une [[Loi de Bernoulli|loi de Bernoulli]] ayant pour valeur 1 (pour pile) et 0 (pour face) et de paramètre $p$, correspondant à la valeur recherchée. Étant donné que l'[[Espérance d'une variable aléatoire|espérance]] d'une loi de Bernoulli est $p$, on choisit comme estimateur de $p$

$$\overline{X} = \frac{1}{n} \sum_{i=1}^n X_i.$$

Remarquons que

$$\begin{aligned} \mathbb{E}[\overline{X}] &= \frac{1}{n} \sum_{i=1}^n \mathbb{E}[X_i] \\ &= \frac{1}{n} \sum_{i=1}^n p \\ &= p \end{aligned}$$

et, les variables $X_1, \dots, X_n$ étant [[Indépendance de variables aléatoires|indépendantes]],

$$\begin{aligned} \mathbb{V}(\overline{X}) &= \frac{1}{n^2} \sum_{i=1}^n \mathbb{V}(X_i) \\ &= \frac{np(1-p)}{n^2} \\ &= \frac{p(1-p)}{n} \\ &\xrightarrow{n \to \infty} 0. \end{aligned}$$

Par conséquent, d'après la [[Condition suffisante de convergence d'un estimateur|condition suffisante de convergence]], $\overline{X}$ est un estimateur convergent de $p$.

En fait, l'exemple précédent est peu pertinent. En effet, s'il présente l'avantage d'être simple, il est restrictif de vérifier uniquement la convergence faible de $\overline{X}$ étant donné que l'on dispose de la [[Loi forte des grands nombres|loi forte des grands nombres]].

**Exemple fondamental.** Soit $(X_n)_n$ une suite de v.a. i.i.d. admettant un moment d'ordre 1 noté $\theta$. On considère $\overline{X}$ pour estimer $\theta$. La loi forte des grands nombres s'applique et nous donne

$$\overline{X} \xrightarrow[n \to \infty]{p.s.} \theta.$$

Ainsi, quelle que soit la loi de la variable mère $X$ (pourvu que $\mathbb{E}[X]$ existe), la [[Moyenne empirique|moyenne empirique]] est un estimateur fortement convergent de $\theta = \mathbb{E}[X]$.

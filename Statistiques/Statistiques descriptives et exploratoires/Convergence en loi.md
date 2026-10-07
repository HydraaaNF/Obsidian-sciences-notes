# Définition

Pour des [[Variable aléatoire discrète|variables aléatoires discrètes]] $X_n$ et $X$ de [[Loi d'une variable aléatoire|lois]] respectives $p_{X_n}$ et $p_X$, la suite $(p_{X_n})$ converge vers $p_X$ lorsque

$$\forall k \in X_n(\Omega) \quad \lim_{n \to +\infty} \mathbb{P}[X_n = k] = \mathbb{P}[X = k]$$

Dans cette situation, on dit que la suite de variables aléatoires réelles $(X_n)$ **converge en loi** vers $X$.

Dans le cas général, dire qu'une suite de lois de probabilité $(p_n)$ converge vers une loi de probabilité $p$ revient à dire que la suite des [[Fonction caractéristique|fonctions caractéristiques]] $(\phi_n)$ correspondantes converge vers la fonction caractéristique de $p$. Ce lien entre convergence des lois et convergence des fonctions caractéristiques fait l'objet du [[Théorème de Paul Lévy]] ; il peut être choisi comme définition de la convergence en loi.

Soit $(X_n)_{n \in \mathbb{N}}$ une suite de [[Variable aléatoire réelle|variables aléatoires réelles]] et $X$ une variable aléatoire réelle, définies sur un même [[Espace probabilisé|espace probabilisé]]. La suite $(X_n)_{n \in \mathbb{N}}$ converge en loi vers $X$ si et seulement si

$$\forall \xi \in \mathbb{R}, \quad \Phi_{X_n}(\xi) \xrightarrow{n \to +\infty} \Phi_X(\xi).$$

On note alors $X_n \xrightarrow{\mathcal{L}} X$.

# Théorème

Soit $(X_n)_{n \in \mathbb{N}}$ une suite de variables aléatoires réelles et $X$ une variable aléatoire réelle, définies sur un même espace probabilisé. La relation hiérarchique suivante entre convergence en probabilité et convergence en loi est admise :

- Si $(X_n)$ converge en [[Convergence en probabilité|probabilité]] vers $X$, alors elle converge en loi vers $X$.
- Réciproquement, si $(X_n)$ converge en loi vers une variable aléatoire constante, alors elle converge en probabilité vers cette constante.

# Remarque

L'étude de la convergence en loi peut s'effectuer sans avoir connaissance de la limite éventuelle, contrairement à celles liées aux convergences en [[Convergence en probabilité|probabilité]] et [[Convergence presque sûre|presque sûre]] qui nécessitent d'avoir une idée de la variable aléatoire limite $X$. Ainsi, compte tenu de la « hiérarchie » entre ces convergences, il peut être judicieux de commencer par étudier la convergence en loi d'une suite de variables aléatoires et de déterminer ainsi la variable aléatoire $X$ qui serait candidate à être la limite de la suite dans le cadre de la convergence faible et/ou forte.

# Exemple

Une suite de variables aléatoires $(X_n)_{n \in \mathbb{N}^*}$ de loi [[Loi binomiale|binomiale]] $\mathcal{B}(n, p_n)$, avec $(p_n)$ tendant vers 0 et $(n p_n)$ tendant vers $\lambda > 0$, converge en loi vers une variable aléatoire de [[Loi de Poisson|loi de Poisson]] $\mathcal{P}(\lambda)$.

Étudions la convergence de la suite $(X_n)_{n \in \mathbb{N}^*}$ où, pour tout $n \in \mathbb{N} \setminus \{0, 1\}$, $X_n(\Omega) = \{-n, 0, n\}$ et

$$\mathbb{P}[X_n = -n] = \mathbb{P}[X_n = n] = \frac{1}{n^2}.$$

Pour tout $\xi \in \mathbb{R}$, pour tout $n \in \mathbb{N}^*$,

$$\begin{aligned}\phi_{X_n}(\xi) &= \frac{e^{-in\xi} + e^{in\xi}}{n^2} + \left(1 - \frac{2}{n^2}\right) \\ &= \frac{2\cos(n\xi)}{n^2} + \left(1 - \frac{2}{n^2}\right) \\ &\xrightarrow{n \to +\infty} 1\end{aligned}$$

Ainsi, la suite $(\Phi_{X_n}(\xi))_{n \in \mathbb{N}^*}$ converge simplement sur $\mathbb{R}$ vers la fonction caractéristique $\Phi_X$ où $X = 0$ p.s. On en déduit que $(X_n)_{n \in \mathbb{N}^*}$ converge en loi vers $X = 0$ p.s. D'après la réciproque de la relation hiérarchique ci-dessus, cette limite étant une variable aléatoire constante, $(X_n)_{n \in \mathbb{N}^*}$ converge en probabilité vers cette constante. Nécessairement, si $(X_n)_{n \in \mathbb{N}^*}$ convergeait presque sûrement, la limite associée serait également $X = 0$ p.s. Soit $\eta > 0$,

$$\begin{aligned}\mathbb{P}[|X_n| > \eta] &\leq \mathbb{P}[|X_n| > 0] \\ &= \frac{2}{n^2}\end{aligned}$$

Grâce à cette majoration, on en déduit que pour tout $\eta > 0$, la série de terme général $\mathbb{P}[|X_n| > \eta]$ converge. D'après le [[Critère de Borel-Cantelli|critère de Borel-Cantelli]], on conclut que $(X_n)_{n \in \mathbb{N}^*}$ converge [[Convergence presque sûre|presque sûrement]] vers $X = 0$ p.s.

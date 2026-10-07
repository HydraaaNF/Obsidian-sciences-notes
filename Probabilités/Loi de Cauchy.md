# Définition

Soit $m$ un réel et $a > 0$. Une [[Variable aléatoire réelle|variable aléatoire réelle]] $X$ suit la **loi de Cauchy** de paramètres $m$ et $a$ si elle admet la [[Probabilité à densité|densité]]

$$f_X(x) = \frac{a}{\pi}\frac{1}{a^2 + (x-m)^2}$$

# Interprétation

Le graphe de la densité est une courbe « en cloche » qui présente un axe de symétrie, la droite d'équation $x = m$. Comme une [[Loi gaussienne|variable aléatoire gaussienne]], une variable aléatoire de Cauchy peut prendre toute valeur réelle ; la comparaison s'arrête là, car la décroissance à l'infini de sa densité est beaucoup moins forte que celle d'une gaussienne.

La symétrie de la densité implique

$$\mathbb{P}(X \leq m) = \frac{1}{2}$$

On dit dans cette situation que $m$ est la **médiane** de $X$. Attention, cela ne signifie pas que $m$ est la moyenne de $X$ : l'[[Espérance d'une variable aléatoire|espérance]] $\mathbb{E}(X)$ n'existe pas. Une variable aléatoire possède toujours une médiane, mais pas toujours une moyenne.

Quant à la dispersion, puisque l'[[Variance|écart-type]] n'existe pas (car si une variable aléatoire n'a pas de [[Moment d'ordre k|moment]] d'ordre 1, elle n'a a fortiori pas de moment d'ordre 2), elle peut être mesurée par le paramètre $a$. En effet, plus $a$ est grand, plus la courbe est « étalée ».

# Propriétés

**Fonction caractéristique.** La transformée de Fourier de $e^{-|x|}$ est

$$\int_{-\infty}^{+\infty} e^{-|x|} e^{ix\xi} \, dx = \frac{2}{1 + \xi^2}$$

La [[Fonction caractéristique|fonction caractéristique]] d'une variable aléatoire $X$ de loi de Cauchy de paramètres $m = 0$ et $a = 1$, qui est la transformée de Fourier de $f_X(x) = \frac{1}{\pi(1+x^2)}$, s'obtient par la formule d'inversion de Fourier :

$$\begin{aligned}\Phi_X(\xi) &= \mathbb{E}(e^{iX\xi}) = \int_{\mathbb{R}} \frac{1}{\pi(1+x^2)} e^{ix\xi} \, dx \\ &= \frac{1}{2\pi} \mathcal{F}\mathcal{F}(e^{-|x|})(-\xi) \\ &= e^{-|\xi|}\end{aligned}$$

Pour des paramètres quelconques, on en déduit

$$\Phi_X(\xi) = e^{im\xi - a|\xi|}$$

# Remarque

C'est la faible décroissance à l'infini de la densité de la loi de Cauchy qui empêche une telle variable aléatoire de posséder des moments : elle constitue un exemple de variable aléatoire **sans moment**. Cela peut choquer, et on pourrait être tenté de dire qu'une variable aléatoire dont la moyenne n'existe pas n'a aucun sens physique. Il n'en est rien, car il est possible de démontrer que le quotient de deux variables aléatoires [[Indépendance de variables aléatoires|indépendantes]] et de même loi $\mathcal{N}(0,1)$ suit la loi de Cauchy de paramètres $m = 0$ et $a = 1$.

# Liens avec d'autres lois

- La loi de Cauchy est stable par somme : si $X \sim \mathcal{C}(m_1, a_1)$ et $Y \sim \mathcal{C}(m_2, a_2)$ sont [[Indépendance de variables aléatoires|indépendantes]], alors $X + Y \sim \mathcal{C}(m_1 + m_2, a_1 + a_2)$.
- La loi de Cauchy est le cas particulier $n = 1$ de la [[Loi de Student]].

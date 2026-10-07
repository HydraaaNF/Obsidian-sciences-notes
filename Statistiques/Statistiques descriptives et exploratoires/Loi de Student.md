# Définition

Pour obtenir l'[[Intervalle de confiance|intervalle de confiance]] pour $m$, on a été amené à introduire une nouvelle loi de probabilités, dite **loi de Student**.

Soient $U$ une [[Loi gaussienne|variable aléatoire]] de loi $\mathcal{N}(0,1)$ et $Y$ une variable aléatoire de loi $\chi_n^2$ ([[Loi du chi-deux]]), [[Indépendance de variables aléatoires|indépendante]] de $U$. La loi de la variable aléatoire

$$T_n = \frac{U}{\sqrt{\frac{Y}{n}}}$$

s'appelle **loi de Student à $n$ degrés de liberté**. On la note $T_n$.

# Interprétation

La loi de Student permet de construire l'[[Intervalle de confiance de la moyenne d'une loi normale de variance inconnue|intervalle de confiance de la moyenne]] d'une [[Loi gaussienne|loi gaussienne]] de variance inconnue ; c'est la loi qui intervient dans le [[Théorème de Student pour la moyenne empirique]].

# Propriétés

Dans la définition précédente, $Y$ est une variable aléatoire positive et $U$ est à valeurs dans $\mathbb{R}$ en entier avec une densité paire, donc $T_n$ est à valeurs dans $\mathbb{R}$ et sa [[Probabilité à densité|densité]] est paire (la loi de Student est symétrique par rapport à 0) :

$$ f_{T_n}(t) = \frac{1}{\sqrt{n}B\left(\frac{1}{2}, \frac{n}{2}\right) \left(1 + \frac{t^2}{n}\right)^{\frac{n+1}{2}}} $$

**Convergence en loi.** De plus, la loi de Student [[Convergence en loi|converge en loi]] vers la loi normale centrée réduite :

$$T_n \xrightarrow{\mathcal{L}} \mathcal{N}(0,1)$$

Ainsi, pour $n \geq 100$, on utilise la table de la loi $\mathcal{N}(0,1)$ à la place de la table de la loi de Student.

**Moments.** Pour $n \geq 2$, $T_n$ admet une [[Espérance d'une variable aléatoire|espérance]] nulle, et pour $n \geq 3$ elle admet également un [[Moment d'ordre k|moment d'ordre 2]] :

$$\mathbb{E}[T_n] = 0 \quad \text{pour } n \geq 2$$

$$\mathbb{V}(T_n) = \frac{n}{n-2} \quad \text{pour } n \geq 3$$

# Liens avec d'autres lois

Cas particulier $n = 1$ : la loi de Student est la [[Loi de Cauchy|loi de Cauchy]], qui est sans [[Moment d'ordre k|moment]].
- Le carré d'une variable aléatoire de loi de Student à $n$ degrés de liberté suit la [[Loi de Fisher|loi de Fisher]] $\mathcal{F}(1, n)$.

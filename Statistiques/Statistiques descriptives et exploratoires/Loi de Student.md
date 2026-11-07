#adm-0bis #adm-9

# Définition

Pour obtenir l'[[Intervalle de confiance|intervalle de confiance]] pour $m$, on a été amené à introduire une nouvelle loi de probabilités, dite **loi de Student**.

Soient $U$ une [[Loi gaussienne|variable aléatoire]] de loi $\mathcal{N}(0,1)$ et $Y$ une variable aléatoire de loi $\chi_n^2$ ([[Loi du chi-deux]]), [[Indépendance de variables aléatoires|indépendante]] de $U$. La loi de la variable aléatoire

$$T_n = \frac{U}{\sqrt{\frac{Y}{n}}}$$

s'appelle **loi de Student à $n$ degrés de liberté**. On la note $T_n$.

# Interprétation

La loi de Student permet de construire l'[[Intervalle de confiance de la moyenne d'une loi normale de variance inconnue|intervalle de confiance de la moyenne]] d'une [[Loi gaussienne|loi gaussienne]] de variance inconnue ; c'est la loi qui intervient dans le [[Théorème de Student pour la moyenne empirique]].

Les tables de cette loi ne donnent pas une probabilité cumulée mais un **quantile bilatéral**. Pour une probabilité $P$ et un nombre de degrés de liberté $n$, la valeur tabulée $t$ vérifie

$$\mathbb{P}(|T_n| \geq t) = P.$$

Le risque $P$ se répartit en deux queues de masse $P/2$ chacune, l'une au-delà de $-t$, l'autre au-delà de $t$ : les deux zones symétriques ont pour aire $P/2$, et leur réunion pour aire $P$. L'intervalle $[-t, t]$ contient donc $T_n$ avec la probabilité $1 - P$.

# Propriétés

Dans la définition précédente, $Y$ est une variable aléatoire positive et $U$ est à valeurs dans $\mathbb{R}$ en entier avec une densité paire, donc $T_n$ est à valeurs dans $\mathbb{R}$ et sa [[Probabilité à densité|densité]] est paire (la loi de Student est symétrique par rapport à 0) :

$$ f_{T_n}(t) = \frac{1}{\sqrt{n}B\left(\frac{1}{2}, \frac{n}{2}\right) \left(1 + \frac{t^2}{n}\right)^{\frac{n+1}{2}}} $$

**Convergence en loi.** De plus, la loi de Student [[Convergence en loi|converge en loi]] vers la loi normale centrée réduite :

$$T_n \xrightarrow{\mathcal{L}} \mathcal{N}(0,1)$$

Ainsi, pour $n \geq 100$, on utilise la table de la loi $\mathcal{N}(0,1)$ à la place de la table de la loi de Student.

**Moments.** Pour $n \geq 2$, $T_n$ admet une [[Espérance d'une variable aléatoire|espérance]] nulle, et pour $n \geq 3$ elle admet également un [[Moment d'ordre k|moment d'ordre 2]] :

$$\mathbb{E}[T_n] = 0 \quad \text{pour } n \geq 2$$

$$\mathbb{V}(T_n) = \frac{n}{n-2} \quad \text{pour } n \geq 3$$

**Valeurs critiques.** Le tableau suivant donne, pour $n$ de 1 à 10 degrés de liberté (en ligne) et pour $P$ de 0,90 à 0,001 (en colonne), la valeur $t$ telle que $\mathbb{P}(|T_n| \geq t) = P$. La lecture à double entrée de ces tables est décrite dans [[Lecture d'une table de probabilité]].

| $\nu \backslash P$ | 0,90 | 0,80 | 0,70 | 0,60 | 0,50 | 0,40 | 0,30 | 0,20 | 0,10 | 0,05 | 0,02 | 0,01 | 0,001 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 0,158 | 0,325 | 0,510 | 0,727 | 1,000 | 1,376 | 1,963 | 3,078 | 6,314 | 12,706 | 31,821 | 63,657 | 636,619 |
| 2 | 0,142 | 0,289 | 0,445 | 0,617 | 0,816 | 1,061 | 1,386 | 1,886 | 2,920 | 4,303 | 6,965 | 9,925 | 31,598 |
| 3 | 0,137 | 0,277 | 0,424 | 0,584 | 0,765 | 0,978 | 1,250 | 1,638 | 2,353 | 3,182 | 4,541 | 5,841 | 12,929 |
| 4 | 0,134 | 0,271 | 0,414 | 0,569 | 0,741 | 0,941 | 1,190 | 1,533 | 2,132 | 2,776 | 3,747 | 4,604 | 8,610 |
| 5 | 0,132 | 0,267 | 0,408 | 0,559 | 0,727 | 0,920 | 1,156 | 1,476 | 2,015 | 2,571 | 3,365 | 4,032 | 6,869 |
| 6 | 0,131 | 0,265 | 0,404 | 0,553 | 0,718 | 0,906 | 1,134 | 1,440 | 1,943 | 2,447 | 3,143 | 3,707 | 5,959 |
| 7 | 0,130 | 0,263 | 0,402 | 0,549 | 0,711 | 0,896 | 1,119 | 1,415 | 1,895 | 2,365 | 2,998 | 3,490 | 5,408 |
| 8 | 0,130 | 0,262 | 0,399 | 0,546 | 0,706 | 0,889 | 1,108 | 1,397 | 1,860 | 2,308 | 2,896 | 3,355 | 5,041 |
| 9 | 0,129 | 0,261 | 0,398 | 0,543 | 0,703 | 0,883 | 1,100 | 1,383 | 1,833 | 2,262 | 2,821 | 3,250 | 4,781 |
| 10 | 0,129 | 0,260 | 0,397 | 0,542 | 0,700 | 0,879 | 1,093 | 1,372 | 1,812 | 2,228 | 2,764 | 3,169 | 4,587 |

# Liens avec d'autres lois

Cas particulier $n = 1$ : la loi de Student est la [[Loi de Cauchy|loi de Cauchy]], qui est sans [[Moment d'ordre k|moment]].
- Le carré d'une variable aléatoire de loi de Student à $n$ degrés de liberté suit la [[Loi de Fisher|loi de Fisher]] $\mathcal{F}(1, n)$.

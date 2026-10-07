# Théorème

Soit $X_1, \dots, X_n$ un [[Échantillon et échantillonnage|échantillon]] de variables aléatoires indépendantes et identiquement distribuées de loi [[Loi gaussienne|gaussienne]] $\mathcal{N}(m, \sigma^2)$. On note $\overline{X}$ la [[Moyenne empirique|moyenne empirique]],

$$\overline{X} = \frac{1}{n} \sum_{i=1}^{n} X_i,$$

et $S^2$, $S'^2$ les estimateurs

- $S^2 = \frac{1}{n} \sum_{i=1}^{n} (X_i - \overline{X})^2$ ;
- $S'^2 = \frac{1}{n-1} \sum_{i=1}^{n} (X_i - \overline{X})^2$,

où $S^2$ est la [[Variance empirique|variance empirique]] et $S'^2$ la variance empirique corrigée. Alors la variable aléatoire réelle

$$\begin{aligned} T_{n-1} &= \frac{\overline{X} - m}{\sqrt{\frac{S'^2}{n}}} \\ &= \sqrt{n}\,\frac{\overline{X} - m}{S'} \\ &= \frac{\overline{X} - m}{\sqrt{\frac{S^2}{n-1}}} \\ &= \sqrt{n-1}\,\frac{\overline{X} - m}{S} \end{aligned}$$

suit une [[Loi de Student|loi de Student]] $\mathcal{T}_{n-1}$ à $n-1$ degrés de liberté.

### Démonstration

Pour un échantillon gaussien, la moyenne empirique vérifie

$$\overline{X} \sim \mathcal{N}\left(m, \frac{\sigma^2}{n}\right).$$

On pose

$$U = \frac{\overline{X} - m}{\sqrt{\frac{\sigma^2}{n}}} = \sqrt{n}\,\frac{\overline{X} - m}{\sigma}$$

et l'on a

$$U \sim \mathcal{N}(0,1).$$

Par ailleurs, on pose

$$Y = \frac{(n-1)S'^2}{\sigma^2}$$

et, d'après la [[Loi de la variance empirique corrigée|loi de la variance empirique corrigée]], $Y$ suit une [[Loi du chi-deux|loi du chi-deux]] à $n-1$ degrés de liberté :

$$Y \sim \chi_{n-1}^2.$$

En supposant $U$ et $Y$ indépendantes, on a, par définition de la loi de Student,

$$\frac{U}{\sqrt{\frac{Y}{n-1}}} \sim \mathcal{T}_{n-1}.$$

En développant et simplifiant l'expression précédente, on obtient

$$\begin{aligned} \frac{U}{\sqrt{\frac{Y}{n-1}}} &= \frac{\left(\sqrt{n}\,\frac{\overline{X} - m}{\sigma}\right)}{\sqrt{\frac{S'^2}{\sigma^2}}} \\ &= \left(\sqrt{n}\,\frac{\overline{X} - m}{\sigma}\right) \left(\frac{\sigma}{S'}\right) \\ &= \sqrt{n}\,\frac{\overline{X} - m}{S'} \end{aligned}$$

c'est-à-dire l'une des écritures équivalentes de $T_{n-1}$ : la variable $T_{n-1}$ suit donc la loi de Student $\mathcal{T}_{n-1}$ à $n-1$ degrés de liberté.

# Remarque

La densité d'une loi de Student est symétrique et sa fonction de répartition est tabulée. Ce résultat est souvent utilisé pour construire un [[Intervalle de confiance de la moyenne d'une loi normale de variance inconnue|intervalle de confiance pour la moyenne]] d'une loi gaussienne de variance inconnue.

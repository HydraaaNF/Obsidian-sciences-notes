#adm-0bis #adm-9

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

# Exemple

On teste $H_0 : m = 30$ contre $H_1 : m \neq 30$ sur un échantillon de $n = 15$ observations, avec $\overline{x} = 37{,}2$ et $s = 6{,}2$.

Sous $H_0$, la statistique prend la valeur

$$t = \sqrt{14}\,\frac{37{,}2 - 30}{6{,}2} = 4{,}35.$$

La valeur critique de $T_{14}$ pour le test bilatéral au risque $\alpha = 0{,}05$ étant $2{,}145$, et $4{,}35 > 2{,}145$, on rejette $H_0$.

# Remarque

La densité d'une loi de Student est symétrique et sa fonction de répartition est tabulée. Ce résultat est souvent utilisé pour construire un [[Intervalle de confiance de la moyenne d'une loi normale de variance inconnue|intervalle de confiance pour la moyenne]] d'une loi gaussienne de variance inconnue.

Lorsque l'écart type $\sigma$ est connu, la statistique standardisée s'écrit directement avec $\sigma$,

$$Z = \frac{\overline{X} - m}{\sigma / \sqrt{n}},$$

et suit une loi normale centrée réduite. Dès que $\sigma$ est inconnu, cette statistique n'est plus calculable : le remplacement de $\sigma$ par l'écart type empirique change la loi de la statistique, qui devient une loi de Student à $n - 1$ degrés de liberté.

Pour un test bilatéral au risque $\alpha$, la valeur critique de $T_{n-1}$ est le quantile d'ordre $1 - \alpha/2$. Dans une table bilatérale, l'en-tête de colonne $P$ désigne la probabilité des deux queues, $P = \mathbb{P}[|T| \geqslant t]$ : cette probabilité se partage en $P/2$ au-delà de $t$ et en $P/2$ en dessous de $-t$, à l'extérieur de l'intervalle $[-t, t]$. La valeur critique d'un test bilatéral au risque $\alpha$ se lit donc dans la colonne $P = \alpha$ ; pour $T_{14}$ et $\alpha = 0{,}05$, elle vaut $2{,}145$. La valeur $1{,}761$ est le quantile d'ordre $0{,}95$, lu dans la colonne $P = 0{,}10$, qui correspond à un test unilatéral au même risque. La lecture à double entrée de ces tables est décrite dans [[Lecture d'une table de probabilité]].

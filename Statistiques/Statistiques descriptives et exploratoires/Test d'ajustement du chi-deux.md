# Définition

Pour l'estimation d'un paramètre à l'aide de la [[Méthode du maximum de vraisemblance|méthode du maximum de vraisemblance]] ou pour le calcul d'un [[Intervalle de confiance|intervalle de confiance]] associé, on suppose la forme (normale, exponentielle, Poisson, etc.) de la loi de la variable aléatoire mère $X$ connue à l'avance. Dans le cas général, on dispose seulement de $n$ observations $x_1, \dots, x_n$ de la loi mère et, à l'aide d'un diagramme représentant la densité empirique, le mieux que l'on puisse faire est d'émettre une hypothèse sur la forme de cette loi $\mathcal{L}$.

Un **test d'ajustement** a pour objectif de tester l'[[Hypothèse nulle et hypothèse alternative|hypothèse nulle]]

$$H_0 : \text{la variable aléatoire mère suit la loi } \mathcal{L}$$

contre l'hypothèse alternative

$$H_1 : \text{la variable aléatoire mère ne suit pas la loi } \mathcal{L}.$$

L'idée est de trouver un critère conduisant à accepter $H_0$ lorsque la « distance » entre la loi empirique (observée sur les $n$ mesures) et la loi théorique supposée n'est pas trop grande : il est logique de rejeter $H_0$ lorsque les mesures obtenues sont « trop éloignées de ce qu'elles devraient être » si le modèle théorique supposé était vrai.

Parmi les tests d'ajustement, le **test du chi-deux** est adapté à une loi $\mathcal{L}$ **discrète ou discrétisée**. On considère une variable aléatoire réelle mère $X$ dont le support est composé de $k$ valeurs (ou $k$ classes) notées $\alpha_1, \dots, \alpha_k$, de probabilités respectives $p_1, \dots, p_k$ sous $H_0$.

Les $n$ observations de la loi mère se répartissent de la façon suivante : $n_1$ mesures ayant la valeur $\alpha_1$, $n_2$ mesures ayant la valeur $\alpha_2$, ..., $n_k$ mesures ayant la valeur $\alpha_k$, avec

$$n_1 + \dots + n_k = n.$$

Ces nombres $n_1, \dots, n_k$ sont les **effectifs observés**. On considère $(x_1, \dots, x_n)$ comme une réalisation de l'[[Échantillon et échantillonnage|échantillon]] $(X_1, \dots, X_n)$ de même loi que la variable aléatoire mère $X$, et on définit les variables aléatoires $N_1, \dots, N_k$ de la façon suivante : pour tout $i \in \{1, \dots, k\}$, $N_i$ correspond, parmi les tirages $X_1, \dots, X_n$, aux effectifs ayant pour valeur $\alpha_i$. Autrement dit, $N_i$ correspond au nombre d'apparitions de $\alpha_i$ lorsque l'on procède à $n$ tirages indépendants issus de la loi mère :

$$N_i(\omega) = \#\{k \in \{1, \dots, n\} \mid X_k(\omega) = \alpha_i\}.$$

Sous $H_0$, la variable aléatoire $N_i$ suit une [[Loi binomiale|loi binomiale]] $\mathcal{B}(n, p_i)$, car les variables aléatoires $X_1, \dots, X_n$ sont indépendantes et ont toutes la même probabilité $p_i$ de prendre la valeur $\alpha_i$. Attention cependant, les variables aléatoires $N_1, \dots, N_k$ ne sont pas indépendantes car

$$N_1 + \dots + N_k = n.$$

Sous $H_0$, parmi $n$ mesures de la loi $\mathcal{L}$, on est en droit d'en attendre une proportion $p_1$ ayant la valeur $\alpha_1$, $p_2$ ayant la valeur $\alpha_2$, etc. Ainsi, si $H_0$ est vérifiée, les **effectifs théoriques** (ou effectifs attendus) pour chaque modalité de la loi mère sont

$$np_1, \dots, np_k.$$

# Théorème

Soit $X$ une variable aléatoire réelle discrète prenant les valeurs $\alpha_1, \dots, \alpha_k$ avec respectivement les probabilités $p_1, \dots, p_k$ (avec $p_1 + \dots + p_k = 1$). Soit $X_1, \dots, X_n$ des variables aléatoires indépendantes et de même loi que $X$. Pour $i \in \{1, \dots, k\}$, on note $N_i$ la variable aléatoire à valeurs dans $\{0, 1, \dots, n\}$ définie par

$$N_i(\omega) = \#\{k \in \{1, \dots, n\} \mid X_k(\omega) = \alpha_i\}.$$

On considère la variable aléatoire $D_n^2$ définie par

$$D_n^2(\omega) = \sum_{i=1}^k \frac{(N_i(\omega) - np_i)^2}{np_i}.$$

Alors la suite de variables aléatoires $(D_n^2)$ [[Convergence en loi|converge en loi]] vers une variable aléatoire de loi $\chi_{k-1}^2$ quand $n$ tend vers $+\infty$.

Autrement dit, $D_n^2$ est approximativement distribuée suivant la [[Loi du chi-deux|loi du chi-deux]] $\chi_{k-1}^2 = \Gamma\left(\frac{k-1}{2}, \frac{1}{2}\right)$ lorsque la taille $n$ de l'échantillon est grande.

# Algorithme

On suppose que l'on dispose d'un grand nombre d'observations de la loi mère et on calcule la valeur de $D_n^2$ observée sur l'échantillon. Pour un [[Risque de première espèce|risque de première espèce]] $\alpha$, on cherche dans la table de la [[Loi du chi-deux|loi du chi-deux]] la valeur $a$ telle que

$$\mathbb{P}_{H_0}[D_n^2 > a] = \alpha.$$

Comme pour le [[Test du chi-deux d'indépendance|test du chi-deux comparant des échantillons décrits par une variable qualitative]], on a alors deux cas :

1. Si la valeur observée de $D_n^2$ est inférieure ou égale à $a$, alors l'événement $[D_n^2 \leq a]$ s'est réalisé. Cet événement avait une probabilité forte (approximativement $1 - \alpha$) de se produire si $X$ suit réellement la loi théorique supposée. Dans ce cas, on n'a aucune raison de rejeter l'hypothèse faite ; par contre on ne connaît pas le risque d'erreur que l'on prend en acceptant cette hypothèse : on peut seulement dire que les mesures faites ne la contredisent pas.
2. Si au contraire la valeur observée de $D_n^2$ est supérieure à $a$, alors l'événement $[D_n^2 > a]$ s'est réalisé. Cet événement avait une probabilité faible (approximativement $\alpha$) de se produire si $X$ suit réellement la loi théorique supposée. La règle de décision consiste à rejeter l'hypothèse faite au motif qu'un tel événement « rare » est « suspect » au point de mettre en doute l'hypothèse de travail $H_0$. La probabilité d'erreur que l'on prend en rejetant l'hypothèse $H_0$, c'est-à-dire la probabilité de rejeter l'hypothèse « $X$ suit la loi $\mathcal{L}$ » alors qu'elle est correcte, est égale à $\alpha$ : c'est la probabilité d'observer la réalisation de l'événement $[D_n^2 > a]$ sous l'hypothèse de travail « $X$ suit la loi $\mathcal{L}$ ».

# Remarque

1. Le test étant basé sur un théorème asymptotique, la loi de $D_n^2$ sous l'hypothèse que $X$ suit la loi $\mathcal{L}$ n'est $\chi_{k-1}^2$ (d'ailleurs approximativement) que lorsque $n$ est grand : on n'utilisera donc le protocole décrit que si $n$ est suffisamment grand (pour fixer les idées, $n \geq 50$).
2. Si $X$ est continue, on la « discrétise » en regroupant ses valeurs en $k$ classes et on est alors ramené au protocole précédent, que l'on applique à la variable aléatoire discrétisée $Y$. Le problème du choix optimal du regroupement en classes est délicat, mais on conseille autant que possible de choisir des classes telles que les effectifs théoriques $np_i$ de chaque classe soient tous (ou presque tous) supérieurs ou égaux à $5$.
3. On peut montrer que si, pour définir la loi théorique $\mathcal{L}$, on a dû estimer $l$ paramètres, alors la loi $\chi_{k-1-l}^2$ approche mieux la loi de $D_n^2$ que la loi $\chi_{k-1}^2$ ; on l'utilisera donc de préférence à $\chi_{k-1}^2$ lors du test.

Lorsque la loi supposée a une densité continue et que tous ses paramètres sont connus, l'ajustement peut également se tester par le [[Test de Kolmogorov-Smirnov]].

# Exemple

**Ajustement à une loi uniforme.** On souhaite savoir si, en 2015-2016, la répartition des étudiants en première année à l'Enssat dans les filières informatique, électronique et photonique suit une [[Loi uniforme discrète|loi uniforme]] (discrète à 3 modalités). D'après leurs fiches de vœux, les 109 étudiants se répartissent de la façon suivante : 42 en informatique, 37 en électronique et 30 en photonique. En supposant que chaque étudiant choisit sa filière indépendamment des autres (hypothèse un peu abusive), on peut effectuer un test du chi-deux (on dispose de 109 mesures). On teste

$$H_0 : \text{le choix de filière suit une loi uniforme sur } \{ \text{info.}, \text{élec.}, \text{photo.} \}$$

contre

$$H_1 : \text{le choix de filière ne suit pas une loi uniforme sur } \{ \text{info.}, \text{élec.}, \text{photo.} \}.$$

Pour simplifier, on note la filière informatique (1), électronique (2) et photonique (3). Sous $H_0$, les effectifs espérés sont environ 36,33 étudiants par filière. Ainsi,

$$\begin{aligned} D_{109}^2 &= \frac{(N_1 - np_1)^2}{np_1} + \frac{(N_2 - np_2)^2}{np_2} + \frac{(N_3 - np_3)^2}{np_3} \\ &= \frac{(N_1 - 36{,}34)^2}{36{,}34} + \frac{(N_2 - 36{,}33)^2}{36{,}33} + \frac{(N_3 - 36{,}33)^2}{36{,}33} \end{aligned}$$

suit approximativement une loi $\chi_2^2$. La valeur observée de cette variable aléatoire est

$$d_{109}^2 = (D_{109}^2)_{\mathrm{obs}} = \frac{(42 - 36{,}34)^2}{36{,}34} + \frac{(37 - 36{,}33)^2}{36{,}33} + \frac{(30 - 36{,}33)^2}{36{,}33} = 1{,}997.$$

Cela contredit-il l'hypothèse de l'équiprobabilité du choix de filière ? Pour $\alpha = 10\%$, on détermine à partir de la table de la loi $\chi_2^2$ le seuil $a = 4{,}605$. Comme la valeur observée de la [[Statistique de test|statistique de test]] $D_{109}^2$ n'est pas dans la [[Zone critique et seuil d'un test|zone critique]], on accepte $H_0$ pour un risque de première espèce $\alpha = 10\%$.

Si l'on teste cette même hypothèse $H_0$ contre $H_1$ pour l'année universitaire 2017-2018, on obtient

$$d_{101}^2 = (D_{101}^2)_{\mathrm{obs}} = \frac{(55 - 33{,}67)^2}{33{,}67} + \frac{(24 - 33{,}67)^2}{33{,}67} + \frac{(22 - 33{,}66)^2}{33{,}66} = 20{,}32.$$

D'après la table de la loi $\chi_2^2$, pour $\alpha = 0{,}05\%$, on a pour valeur de seuil de la zone critique $a = 15{,}202$. Comme $d_{101}^2 > 15{,}202$, on rejette $H_0$ avec un risque de se tromper très faible (inférieur à 0,05 %).

**Ajustement à une loi exponentielle.** Soit $X$ la variable aléatoire correspondant à la durée de vie d'un composant électronique. En [[Fiabilité|fiabilité]], on considère souvent un modèle exponentiel pour la loi de $X$. Le fabricant fait mesurer la durée de vie de 200 composants tirés au hasard. Sur ces 200 mesures, on obtient $\bar{x} = 500$ jours et les résultats sont répartis de la façon suivante :

| Classe | $[0, 200[$ | $[200, 400[$ | $[400, 600[$ | $[600, 800[$ | $[800, 1200[$ | $[1200, +\infty[$ |
|---|---|---|---|---|---|---|
| Effectifs | 61 | 48 | 33 | 23 | 20 | 15 |

On teste $H_0$ : $X$ suit une [[Loi exponentielle|loi exponentielle]] contre $H_1$ : $X$ ne suit pas une loi exponentielle.

On estime le paramètre $\lambda$ par $\frac{1}{\bar{x}}$ et on calcule les effectifs théoriques de chaque classe ci-dessus :

$$\begin{aligned}
p_1 &= \mathbb{P}_{H_0}[X \leq 200] \\
&= \int_0^{200} \lambda e^{-\lambda x}\,dx \\
&= 1 - e^{-\lambda 200} \\
&= 1 - e^{-200/500} \\
&= 0{,}33
\end{aligned}$$

Les autres probabilités et les effectifs théoriques correspondants sont :

| Classe | $p_i$ | $np_i$ |
|---|---|---|
| 1 | 0,33 | 66 |
| 2 | $e^{-200/500} - e^{-400/500} = 0{,}22$ | 44 |
| 3 | $e^{-400/500} - e^{-600/500} = 0{,}15$ | 30 |
| 4 | $e^{-600/500} - e^{-800/500} = 0{,}10$ | 20 |
| 5 | $e^{-800/500} - e^{-1200/500} = 0{,}11$ | 22 |
| 6 | $\mathbb{P}_{H_0}[X \geq 1200] = 0{,}09$ | 18 |

Tous les effectifs théoriques étant supérieurs ou égaux à $5$, on n'effectue pas de regroupements de classe. Sous $H_0$, $\mathcal{D}_{200}^2$ suit approximativement une loi $\chi_{6-1-1}^2 = \chi_4^2$, car il y a $6$ classes et un seul paramètre a été estimé.

$$\begin{aligned}
(\mathcal{D}_{200}^2)_{\mathrm{obs}} &= \sum_{i=1}^{6} \frac{(n_i - np_i)^2}{np_i} \\
&= \frac{(61 - 66)^2}{66} + \frac{(48 - 44)^2}{44} + \frac{(33 - 30)^2}{30} + \frac{(23 - 20)^2}{20} + \frac{(20 - 22)^2}{22} + \frac{(15 - 18)^2}{18} \\
&= 2{,}174.
\end{aligned}$$

*Remarque :* dans cet exemple, même si l'on avait calculé la [[Variance empirique|variance empirique]] ou la [[Médiane empirique|médiane]], le nombre de paramètres estimés reste $l = 1$ car seul un paramètre (la valeur estimée de $\lambda$) est nécessaire pour calculer les effectifs théoriques.

Pour un risque de première espèce $\alpha = 10\%$, la zone critique est $]7{,}779, +\infty[$ d'après la table de la loi $\chi_4^2$. Comme $(\mathcal{D}_{200}^2)_{\mathrm{obs}} \leq 7{,}779$, on accepte $H_0$ et on affirme que la loi mère est exponentielle.

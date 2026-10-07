# Définition

Le **test de Kolmogorov-Smirnov** est un test réservé à l'ajustement de données à une loi de probabilité avec une **densité continue** (c'est-à-dire une fonction de répartition $F_0$ de classe $\mathcal{C}^1$) **connue** (c'est-à-dire dont tous les éventuels paramètres sont connus et ne nécessitent pas d'être estimés).

On observe $(x_1, \dots, x_n)$ issu de l'[[Échantillon et échantillonnage|échantillon]] $(X_1, \dots, X_n)$ dont la loi mère a pour fonction de répartition $F$. On teste les [[Hypothèse nulle et hypothèse alternative|hypothèses nulle et alternative]]

$$H_0 : F = F_0 \quad \text{contre} \quad H_1 : F \neq F_0.$$

On considère la [[Fonction de répartition empirique|fonction de répartition empirique]] $F_n$ associée à $(x_1, \dots, x_n)$. Afin de calculer $F_n$, on range les observations $x_1, \dots, x_n$ par ordre croissant et on note $(x_{(1)}, \dots, x_{(n)})$ le $n$-uplet ainsi obtenu. La fonction $F_n$ est définie par

$$F_n = \begin{cases}
0 & \text{si } x < x_{(1)} \\
\frac{1}{n} & \text{si } x = x_{(1)} \\
\frac{i}{n} & \text{si } x_{(i-1)} < x \leq x_{(i)} \text{ pour } i \in \{2, \dots, n\} \\
1 & \text{si } x > x_{(n)}
\end{cases}$$

# Théorème

La [[Statistique de test|statistique de test]] est l'écart maximal entre $F_n$ et $F_0$ :

$$\mathcal{D}_n = \sup_{x \in \mathbb{R}} |F_n(x) - F_0(x)|$$

Elle vérifie, sous $H_0$, pour tout $y \geq 0$,

$$\mathbb{P}\left[\sqrt{n}\,\mathcal{D}_n < y\right] \xrightarrow{n\to\infty} K(y) = \sum_{k=-\infty}^{+\infty} (-1)^k e^{-2k^2y^2}$$

où la fonction $K$ est une fonction tabulée. Si $H_0$ n'est pas vérifiée, alors

$$\sqrt{n}\mathcal{D}_n \xrightarrow{n \rightarrow \infty} + \infty.$$

# Remarque

Comme $F_n$ est une fonction discontinue, le calcul de $\mathcal{D}_n$ s'effectue de la façon suivante :

$$\mathcal{D}_n = \max \left\{ \max \left\{ \left| \frac{i}{n} - F_0(x_{(i)}) \right| ; \left| \frac{i-1}{n} - F_0(x_{(i)}) \right| \right\} \middle| i \in \{1, \dots, n\} \right\}$$

Lorsque des paramètres de la loi sous $H_0$ doivent être estimés, on recourt au [[Test d'ajustement du chi-deux]].

Pour une loi exponentielle de paramètre $2$, la fonction de répartition s'écrit $F_0(x) = (1 - e^{-2x}) \mathbf{1}_{[0, +\infty[}(x)$. La forme $F_0(x) = (1 - e^{2x}) \mathbf{1}_{[0, +\infty[}(x)$, avec un exposant positif, est une erreur fréquente : $1 - e^{2x}$ est décroissante et négative dès que $x > 0$, alors qu'une fonction de répartition est croissante et à valeurs dans $[0, 1]$ ; les valeurs numériques du tableau de l'exemple imposent elles aussi l'exposant négatif (par exemple $1 - e^{-2 \times 0{,}36} = 0{,}513$).

# Exemple

On dispose d'un échantillon de 6 observations et on souhaite tester leur ajustement avec une [[Loi exponentielle|loi exponentielle]] de paramètre 2. Autrement dit, on teste

$H_0$ : la loi mère a pour fonction de répartition $F_0(x) = (1 - e^{-2x}) \mathbf{1}_{[0, +\infty[}(x)$

contre $H_1$ : la loi mère a une fonction de répartition différente de $F_0$.

Le tableau suivant donne le calcul de la statistique $\mathcal{D}_6$ :

| $i$ | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|
| $x_{(i)}$ | 0,36 | 0,51 | 0,69 | 0,92 | 1,20 | 2,32 |
| $F_0(x_{(i)})$ | 0,513 | 0,639 | 0,748 | 0,841 | 0,909 | 0,990 |
| $\frac{i}{n}$ | $\frac{1}{6}$ | $\frac{2}{6}$ | $\frac{3}{6}$ | $\frac{4}{6}$ | $\frac{5}{6}$ | 1 |
| $\left\lvert \frac{i}{n} - F_0(x_{(i)}) \right\rvert$ | 0,346 | 0,305 | 0,248 | 0,174 | 0,075 | 0,009 |
| $\left\lvert \frac{i-1}{n} - F_0(x_{(i)}) \right\rvert$ | **0,513** | 0,472 | 0,414 | 0,341 | 0,242 | 0,157 |

Pour un [[Risque de première espèce|risque de première espèce]] $\alpha = 0{,}1$, on cherche une [[Zone critique et seuil d'un test|zone critique]] de la forme $]a, +\infty[$ où $a$ vérifie

$$\mathbb{P} \left[ \mathcal{D}_6 > a \right] = \alpha$$

c'est-à-dire $K(\sqrt{6}a) \simeq 1 - \alpha$, bien que $n = 6$ soit assez faible. Dans la table de la loi de Kolmogorov-Smirnov, on lit directement $a = 0{,}467$. D'après le tableau ci-dessus, la valeur observée de $\mathcal{D}_6$ vaut 0,513 et se trouve dans la zone critique. On rejette par conséquent $H_0$ au risque de première espèce $\alpha = 0{,}1$.

# Loi

La loi exponentielle est une [[Probabilité à densité|loi à densité]] qui modélise des durées de vie telles que :

- le temps entre deux arrivées successives de tâches dans un [[Processus de Poisson|processus de Poisson]] ;
- le temps de service à un serveur dans un réseau de [[File d'attente|files d'attente]] ;
- le temps avant la panne d'un composant.

Pour une [[Variable aléatoire continue|variable aléatoire continue]] $X$ suivant une loi exponentielle de paramètre $\lambda > 0$, la densité $f$ et la [[Fonction de répartition|fonction de répartition]] $F$ s'écrivent, pour $x \geq 0$,

$$f(x) = \lambda e^{-\lambda x}$$

$$F(x) = 1 - e^{-\lambda x}.$$

# Propriétés

- Son [[Espérance d'une variable aléatoire|espérance]] est $\mathbb{E}[X] = \lambda^{-1}$ et sa [[Variance|variance]] est $\mathbb{V}[X] = \lambda^{-2}$.

Sa [[Fonction caractéristique|fonction caractéristique]] vaut

$$\Phi_X(\xi) = \frac{\lambda}{\lambda - i\xi}.$$

**Absence de mémoire.** En [[Fiabilité|fiabilité]], $R(t)$ désigne la probabilité qu'un individu survive au-delà de $t$ :

$$R(t) = \mathbb{P}[X > t].$$

La probabilité qu'un individu meure entre $t_1$ et $t_2$, sachant qu'il est vivant en $t_1$, est la [[Probabilité conditionnelle|probabilité conditionnelle]]

$$\mathbb{P}[t_1 \leq X < t_2 \mid X > t_1] = \frac{R(t_1) - R(t_2)}{R(t_1)}.$$

Pour la loi exponentielle, $R(t) = e^{-ct}$, où $c$ est le paramètre de taux de la loi (noté $\lambda$ ci-dessus), d'où

$$\mathbb{P}[t_1 \leq X < t_2 \mid X > t_1] = 1 - e^{-c(t_2 - t_1)} = \mathbb{P}[X < t_2 - t_1].$$

# Interprétation

La densité décroît à partir de $f(0) = \lambda$ : plus le paramètre $\lambda$ est grand, plus la durée de vie est concentrée près de $0$. La fonction de répartition, elle, croît de $0$ vers $1$.

Densité $f(x) = \lambda e^{-\lambda x}$ pour trois valeurs du paramètre (valeurs calculées à partir de la formule ci-dessus, arrondies à $10^{-4}$) :

```chart
type: line
labels: ["0", "0.5", "1", "1.5", "2", "2.5", "3", "3.5", "4", "4.5", "5"]
series:
  - title: λ = 0.5
    data: [0.5, 0.3894, 0.3033, 0.2362, 0.1839, 0.1433, 0.1116, 0.0869, 0.0677, 0.0527, 0.041]
  - title: λ = 1
    data: [1.0, 0.6065, 0.3679, 0.2231, 0.1353, 0.0821, 0.0498, 0.0302, 0.0183, 0.0111, 0.0067]
  - title: λ = 1.5
    data: [1.5, 0.7085, 0.3347, 0.1581, 0.0747, 0.0353, 0.0167, 0.0079, 0.0037, 0.0018, 0.0008]
```

Fonction de répartition $F(x) = 1 - e^{-\lambda x}$ pour les mêmes valeurs :

```chart
type: line
labels: ["0", "0.5", "1", "1.5", "2", "2.5", "3", "3.5", "4", "4.5", "5"]
series:
  - title: λ = 0.5
    data: [0.0, 0.2212, 0.3935, 0.5276, 0.6321, 0.7135, 0.7769, 0.8262, 0.8647, 0.8946, 0.9179]
  - title: λ = 1
    data: [0.0, 0.3935, 0.6321, 0.7769, 0.8647, 0.9179, 0.9502, 0.9698, 0.9817, 0.9889, 0.9933]
  - title: λ = 1.5
    data: [0.0, 0.5276, 0.7769, 0.8946, 0.9502, 0.9765, 0.9889, 0.9948, 0.9975, 0.9988, 0.9994]
```

La probabilité conditionnelle de mourir dans un intervalle de durée donnée ne dépend pas de l'instant $t_1$ déjà atteint : un individu déjà vivant en $t_1$ a la même loi de durée de vie résiduelle qu'un individu neuf : il ne vieillit pas.

# Liens avec d'autres lois

- La loi exponentielle est un cas particulier de la [[Loi gamma|loi gamma]].
- Elle est généralisée par la [[Loi de Weibull|loi de Weibull]].
- La somme de $n$ variables aléatoires [[Indépendance de variables aléatoires|indépendantes]] et identiquement distribuées de loi exponentielle de paramètre $\lambda$ suit la [[Loi gamma|loi gamma]] $\Gamma(n, \lambda)$.
- Le minimum de $n$ variables aléatoires indépendantes de lois exponentielles de paramètres $\lambda_1, \dots, \lambda_n$ suit une loi exponentielle de paramètre $\lambda_1 + \dots + \lambda_n$.
- Si $U$ suit la [[Loi uniforme continue|loi uniforme continue]] sur $[0, 1]$, alors $-\frac{\ln(U)}{\lambda}$ suit la loi exponentielle de paramètre $\lambda$.
- Si $X$ suit la loi exponentielle de paramètre $\lambda$ et $c > 0$, alors $cX$ suit la loi exponentielle de paramètre $\lambda/c$.
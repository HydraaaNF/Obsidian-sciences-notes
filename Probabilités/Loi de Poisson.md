# Définition

La loi de Poisson $\mathcal{P}(\alpha)$ est une loi de [[Probabilité discrète|probabilité discrète]] définie par

$$\mathbb{P}[X = k] = \frac{\alpha^k e^{-\alpha}}{k!}$$

Elle donne la probabilité d'observer $k$ événements se produisant à un taux $\lambda$ sur un intervalle de durée $t$, le paramètre valant alors $\alpha = \lambda t$ : c'est la loi du nombre d'événements d'un [[Processus de Poisson|processus de Poisson]] de taux $\lambda$.

# Propriétés

- Son [[Espérance d'une variable aléatoire|espérance]] et sa [[Variance|variance]] sont égales : $\mathbb{E}[X] = \mathbb{V}[X] = \alpha$.

Sa [[Fonction génératrice|fonction génératrice]] vaut

$$G_X(z) = \mathbb{E}(z^X) = e^{\alpha(z-1)}.$$

# Interprétation

Pour de petites valeurs de $\alpha$, la masse est concentrée au voisinage de $0$ et la distribution est fortement asymétrique ; quand $\alpha$ augmente, la distribution se déplace vers des valeurs plus grandes et s'étale autour de $\alpha$, tandis que la fonction de répartition se rapproche de $1$.

Fonction de masse $\mathbb{P}[X = k]$ pour trois valeurs du paramètre (valeurs calculées à partir de la formule de la définition, arrondies à $10^{-4}$) :

```chart
type: line
labels: ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "10", "11", "12", "13", "14", "15", "16", "17", "18", "19", "20"]
series:
  - title: α = 1
    data: [0.3679, 0.3679, 0.1839, 0.0613, 0.0153, 0.0031, 0.0005, 0.0001, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
  - title: α = 4
    data: [0.0183, 0.0733, 0.1465, 0.1954, 0.1954, 0.1563, 0.1042, 0.0595, 0.0298, 0.0132, 0.0053, 0.0019, 0.0006, 0.0002, 0.0001, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
  - title: α = 10
    data: [0.0, 0.0005, 0.0023, 0.0076, 0.0189, 0.0378, 0.0631, 0.0901, 0.1126, 0.1251, 0.1251, 0.1137, 0.0948, 0.0729, 0.0521, 0.0347, 0.0217, 0.0128, 0.0071, 0.0037, 0.0019]
```

Fonction de répartition $\mathbb{P}[X \leq k]$ pour trois valeurs du paramètre :

```chart
type: line
labels: ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "10", "11", "12", "13", "14", "15", "16", "17", "18", "19", "20"]
series:
  - title: α = 1
    data: [0.3679, 0.7358, 0.9197, 0.981, 0.9963, 0.9994, 0.9999, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0]
  - title: α = 4
    data: [0.0183, 0.0916, 0.2381, 0.4335, 0.6288, 0.7851, 0.8893, 0.9489, 0.9786, 0.9919, 0.9972, 0.9991, 0.9997, 0.9999, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0]
  - title: α = 10
    data: [0.0, 0.0005, 0.0028, 0.0103, 0.0293, 0.0671, 0.1301, 0.2202, 0.3328, 0.4579, 0.583, 0.6968, 0.7916, 0.8645, 0.9165, 0.9513, 0.973, 0.9857, 0.9928, 0.9965, 0.9984]
```

# Liens avec d'autres lois

- La loi de Poisson fournit une approximation de la [[Loi binomiale|loi binomiale]] pour $p$ petit et $n$ grand ($n \geq 20$, $p \leq 0.05$) : la loi binomiale $\mathcal{B}(n, p)$ est approchée par la loi de Poisson de paramètre $\alpha = np$.
- La somme de deux variables aléatoires [[Indépendance de variables aléatoires|indépendantes]] de lois de Poisson suit une loi de Poisson : si $X \sim \mathcal{P}(\alpha)$ et $Y \sim \mathcal{P}(\beta)$, alors $X + Y \sim \mathcal{P}(\alpha + \beta)$.
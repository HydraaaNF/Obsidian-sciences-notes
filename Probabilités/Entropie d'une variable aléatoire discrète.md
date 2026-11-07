#adm-8

# Définition

L'entropie d'une variable aléatoire discrète $X$ est l'[[Espérance d'une variable aléatoire|espérance]] de la quantité d'information apportée par l'évènement observé : à chaque valeur $x_i$ de probabilité $\mathbb{P}(x_i)$, on associe l'information $-\log_b \mathbb{P}(x_i)$, et l'entropie est la moyenne de cette quantité.

$$H(X) = \mathbb{E}[-\log_b \mathbb{P}(x)] = -\sum_i \mathbb{P}(x_i)\log_b \mathbb{P}(x_i),$$

où la somme porte sur les valeurs $x_i$ prises par $X$ et où $b > 1$ est la base du logarithme.

# Interprétation

L'entropie mesure l'incertitude moyenne portée par la loi de $X$ : c'est la quantité moyenne d'information, au sens de la définition précédente, que la distribution fournit. Plus la loi est concentrée, plus l'entropie est faible ; plus l'incertitude sur la valeur prise par $X$ est grande, plus l'entropie est élevée.

# Propriétés

- Si $X$ est déterministe, c'est-à-dire si une de ses valeurs est de probabilité $1$ et toutes les autres de probabilité $0$, l'entropie est nulle : $H(X) = 0$.
- Si $X$ suit une [[Loi uniforme discrète|loi uniforme]] sur $n$ issues équiprobables, chaque terme vaut $\frac{1}{n}\log_b n$ et l'entropie vaut $H(X) = \log_b n$.
- Pour $n = 2$ issues équiprobables et $b = 2$, on retrouve $\log_2 2 = 1$ : c'est le cas où l'entropie vaut $1$.

# Exemple

Processus de Bernoulli : on lance une pièce et on note $X$ la variable valant $1$ pour pile, avec $\mathbb{P}[X = \text{pile}] = p$. La [[Loi de Bernoulli|loi de Bernoulli]] de paramètre $p$ donne

$$H(X) = -p\log_b p - (1-p)\log_b(1-p),$$

en convenant que $p\log_b p = 0$ pour $p = 0$ ou $p = 1$. En faisant varier $p$ de $0$ à $1$, on obtient la courbe suivante, tracée en base $2$ : l'entropie part de $0$ pour $p = 0$ et $p = 1$, où le résultat est certain, et culmine à $1$ en $p = \frac{1}{2}$, où les deux issues sont équiprobables.

```chart
type: line
labels: ["0", "0.1", "0.2", "0.3", "0.4", "0.5", "0.6", "0.7", "0.8", "0.9", "1.0"]
series:
  - title: Entropie de la loi de Bernoulli de paramètre p
    data: [0, 0.47, 0.72, 0.88, 0.97, 1.0, 0.97, 0.88, 0.72, 0.47, 0]
```

# Remarque

Pour une loi uniforme sur $n$ issues équiprobables, l'entropie vaut $\log_b n$ ; l'écriture « une loi uniforme a une entropie de $1$ » est un raccourci qui ne vaut que dans le cas particulier où $n = b$, par exemple deux issues équiprobables en base $2$ ($\log_2 2 = 1$). En toute généralité, c'est la formule $H(X) = -\sum_i \mathbb{P}(x_i)\log_b \mathbb{P}(x_i)$ qui fait foi.

L'entropie se généralise au conditionnement en [[Entropie conditionnelle]] ; rechercher la loi d'entropie maximale sous des contraintes est l'objet du [[Principe du maximum d'entropie]].

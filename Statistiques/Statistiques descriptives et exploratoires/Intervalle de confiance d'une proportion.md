# Définition

Considérons une population de $N$ individus dont une proportion $p \in [0,1]$ vérifie une certaine propriété $\mathcal{P}$. Si $N$ est très grand, il est impossible de connaître exactement $p$, et l'on a alors recours à un *sondage* : on tire au hasard et indépendamment $n$ individus, avec $n$ nettement inférieur à $N$ (sinon la méthode n'a aucun intérêt), et on regarde s'ils satisfont la propriété $\mathcal{P}$. On obtient les mesures $x_1, \dots, x_n$ telles que

$$x_i = \begin{cases} 1 & \text{si le } i\text{-ème individu vérifie la propriété } \mathcal{P} \\ 0 & \text{sinon.} \end{cases}$$

La **fréquence empirique** $f$ est la proportion d'individus vérifiant la propriété $\mathcal{P}$ observée sur les $n$ individus sondés :

$$f = \frac{x_1 + \dots + x_n}{n}.$$

# Propriétés

À chaque individu sondé, on peut associer une [[Loi de Bernoulli|variable aléatoire de Bernoulli]] qui vaut $1$ s'il vérifie la propriété $\mathcal{P}$ et $0$ sinon. En vertu des hypothèses du sondage, on obtient ainsi une suite $X_1, \dots, X_n$ de variables de Bernoulli indépendantes et de même paramètre $p$ :

$$\forall i \in \{1, \dots, n\}, \quad \mathbb{P}[X_i = 1] = p,$$

car la probabilité qu'un individu choisi au hasard dans la population vérifie la propriété $\mathcal{P}$ est égale à la proportion d'individus vérifiant $\mathcal{P}$. On souhaite donc estimer par intervalle

$$p = \mathbb{E}(X),$$

où $X$ est une variable aléatoire de loi $\mathcal{B}(p)$.

L'[[Estimateur|estimateur]] utilisé est

$$\overline{X} = F = \frac{1}{n} \sum_{i=1}^n X_i,$$

qui représente aussi bien la [[Moyenne empirique|moyenne empirique]] des $X_i$ que la fréquence empirique. Cet estimateur de $p$ est [[Estimateur fortement convergent|fortement convergent]], [[Biais d'un estimateur|sans biais]] et [[Estimateur efficace|efficace]].

On remarque que

$$n\overline{X} = \sum_{i=1}^n X_i \sim \mathcal{B}(n,p),$$

puisque l'on somme $n$ variables de Bernoulli indépendantes et de même paramètre $p$. La [[Loi binomiale|loi binomiale]] est cependant difficile à exploiter, même à l'aide d'une table : on se place donc dans le cas où la taille $n$ de l'échantillon est grande. Le [[Théorème de la limite centrale|théorème de la limite centrale]] s'applique alors, et l'estimation de $p$ apparaît comme un cas particulier de l'[[Intervalle de confiance de la moyenne d'une loi quelconque|estimation d'une moyenne par intervalle]], avec $\overline{x} = f$.

Comme estimation de $\sigma^2 = p(1-p)$, on peut choisir $s$ plutôt que $s'$ puisque $n$ est grand. Or, dans le cas présent,

$$\begin{aligned} s^2 &= \overline{x^2} - \overline{x}^2 \\ &= \frac{1}{n} \sum_{i=1}^{n} x_i^2 - f^2 \\ &= \frac{1}{n} \sum_{i=1}^{n} x_i - f^2 \\ &= f - f^2 \\ &= f(1 - f) \end{aligned}$$

En effet, pour une variable de Bernoulli ne pouvant prendre que les valeurs $0$ ou $1$, on a $X_i^2 = X_i$. Cela revient à estimer

- $p = \mathbb{E}(X)$ par $F$ ;
- $p(1-p) = \mathbb{V}(X)$ par $F(1-F)$,

ce qui est somme toute logique.

Finalement, l'[[Intervalle de confiance|intervalle de confiance]] de niveau $1 - \alpha$ pour la proportion $p$ est

$$\left[ f - u_{\frac{\alpha}{2}} \sqrt{\frac{f(1-f)}{n}} , f + u_{\frac{\alpha}{2}} \sqrt{\frac{f(1-f)}{n}} \right],$$

où $u_{\frac{\alpha}{2}}$ est le [[Quantile de la loi normale centrée réduite|quantile de la loi normale centrée réduite]].

# Exemple

On considère un candidat $A$ en lice pour une élection, la propriété $\mathcal{P}$ étant « vote pour $A$ ». Pour estimer $p$, qui représente dans ce contexte le score véritable du candidat $A$ le jour des élections, on effectue un sondage et $f$ est alors le score observé à l'avance sur $n$ individus. Il est intuitivement clair que $f$ est un bon estimateur de $p$ sous les conditions que la population totale soit suffisamment stabilisée dans ses choix le jour du sondage, et que les individus sondés aient été choisis « totalement au hasard », c'est-à-dire de façon uniforme et indépendamment les uns des autres.

# Remarque

L'intervalle de confiance obtenu est un intervalle approché : sa construction suppose une grande taille $n$ d'échantillon.

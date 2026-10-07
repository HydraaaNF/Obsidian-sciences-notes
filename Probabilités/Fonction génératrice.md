# Définition

Soient $(\Omega, \mathcal{F}, \mathbb{P})$ un [[Espace probabilisé|espace probabilisé]] et $X$ une [[Variable aléatoire réelle|variable aléatoire réelle]] définie sur $\Omega$ telle que $X(\Omega) \subset \mathbb{N}$. On appelle **fonction génératrice** de $X$ la fonction $G_X$ définie par

$$G_X(z) = \mathbb{E}(z^X) = \sum_{n \in \mathbb{N}} \mathbb{P}(X = n) z^n$$

# Interprétation

La fonction génératrice est un outil analytique facilitant l'étude des variables aléatoires à valeurs dans $\mathbb{N}$. Elle ramène l'étude de notions probabilistes pouvant être délicates (par exemple la recherche de la loi de la somme de variables aléatoires [[Indépendance de variables aléatoires|indépendantes]]) à du calcul sur des séries entières.

# Exemple

**Loi de Poisson.** Si $X$ suit la [[Loi de Poisson|loi de Poisson]] de paramètre $\lambda$, alors :

$$G_X(z) = \sum_{n \in \mathbb{N}} z^n e^{-\lambda} \frac{\lambda^n}{n!} = e^{-\lambda} \sum_{n \in \mathbb{N}} \frac{(z\lambda)^n}{n!} = e^{-\lambda} e^{\lambda z} = e^{\lambda(z-1)}$$

# Propriétés

La fonction génératrice $G_X$ est la somme d'une série entière : elle est définie pour tout complexe $z$ dont le module est inférieur au rayon de convergence $R$ de cette série entière. Or cette série converge pour $z = 1$ puisque $\sum_{n \in \mathbb{N}} \mathbb{P}(X = n) = 1$, donc elle converge aussi pour tout $z$ tel que $|z| \leq 1$ (convergence absolue de la série entière), donc $R \geq 1$.

Dans l'exemple précédent, le rayon de convergence est $R = +\infty$, car le calcul est valable pour tout $z \in \mathbb{C}$. Il existe des variables aléatoires pour lesquelles le rayon de convergence est $R = 1$.

On peut considérer la fonction génératrice comme la « **transformée en $z$** » (au détail près de l'exposant $n$ au lieu de $-n$) de la suite $(\mathbb{P}(X = n))_{n \in \mathbb{N}}$ donnant la loi de $X$.

Par ailleurs, puisque $X(\Omega) \subset \mathbb{N}$ avec $\mathbb{P}(X = n) = 0$ si $n \notin X(\Omega)$, on a aussi

$$G_X(z) = \sum_{n \in X(\Omega)} \mathbb{P}(X = n) z^n$$

**Caractérisation de la loi.** On peut retrouver la loi $p_X$ à partir de $G_X(z)$ : la fonction génératrice caractérise la [[Loi d'une variable aléatoire|loi]] d'une variable aléatoire à valeurs dans $\mathbb{N}$. En effet, il suffit de développer $G_X(z)$ en série entière et d'identifier les coefficients pour retrouver $\mathbb{P}(X = n)$, à moins, ce qui est encore plus simple, que l'on reconnaisse la fonction génératrice d'une loi usuelle. Si les développements en série entière usuels ne permettent pas d'identifier rapidement $\mathbb{P}(X = n)$, on peut appliquer le résultat suivant, conséquence de la formule de Taylor : voir [[Formule de Taylor]].

### Lien avec les moments

On peut dériver terme à terme une série entière à l'intérieur du disque de convergence. Cela permet d'obtenir les [[Moment d'ordre k|moments]] de $X$ par dérivation de $G_X$. Par exemple :

$$\mathbb{E}(X) = \sum_{n \in \mathbb{N}^*} n \, \mathbb{P}(X = n)$$

et par ailleurs, dans le disque de convergence :

$$G'_X(z) = \sum_{n \in \mathbb{N}^*} n \, \mathbb{P}(X = n) z^{n-1}$$

de sorte que, formellement :

$$\mathbb{E}(X) = G'_X(1)$$

- Si le rayon de convergence est supérieur à $1$, le remplacement de $z$ par $1$ est autorisé, et l'on a donc bien l'existence de l'[[Espérance d'une variable aléatoire|espérance]] $\mathbb{E}(X)$ et la formule $\mathbb{E}(X) = G'_X(1)$.
- Si le rayon de convergence est égal à $1$, on a peut-être $\mathbb{E}(X) = +\infty$. Si $\mathbb{E}(X) < +\infty$, alors la série entière dérivée converge en $z = 1$, et le théorème d'Abel permet d'obtenir $\mathbb{E}(X)$ par un passage à la limite :

$$\mathbb{E}(X) = \lim_{x \to 1^-} G'_X(x)$$

# Théorème

**Fonction génératrice d'une somme de variables aléatoires indépendantes.** La fonction génératrice permet souvent d'obtenir très facilement la loi de la somme de deux variables aléatoires discrètes indépendantes. Soient $X$ et $Y$ des variables aléatoires réelles définies sur le même espace probabilisé et à valeurs dans $\mathbb{N}$. On suppose que $X$ et $Y$ sont [[Indépendance de variables aléatoires|indépendantes]]. Alors :

$$G_{X+Y}(z) = G_X(z) G_Y(z)$$

# Remarque

**Cas des variables aléatoires à valeurs dans $\mathbb{Z}$.** On peut essayer de définir $G_X(z)$ par la somme $\sum_{n \in X(\Omega)} \mathbb{P}(X = n) z^n$, mais si $\mathbb{P}(X = n) \neq 0$ pour une infinité de $n < 0$ **et** pour une infinité de $n > 0$, il peut arriver que l'ensemble de définition de $G_X$ soit vide. En effet, dans ce cas, l'ensemble de définition de $G_X$ est une *couronne* centrée en $0$, couronne qui peut être vide lorsque les conditions de convergence des deux séries $\sum_{n < 0} \mathbb{P}(X = n) z^n$ et $\sum_{n \geq 0} \mathbb{P}(X = n) z^n$ sont incompatibles. Il s'agit alors de séries de Laurent (transformées en $z$ bilatérales), valables dans une couronne.

Un outil analytique analogue pour une variable aléatoire réelle quelconque est la [[Fonction caractéristique]].

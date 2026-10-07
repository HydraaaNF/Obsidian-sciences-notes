# Définition

Soit $(\Omega, \mathcal{F}, \mathbb{P})$ un [[Espace probabilisé|espace probabilisé]] et $E$ un ensemble **fini ou dénombrable**. Toute application $X$ de $\Omega$ dans $E$ :

$$X : \Omega \longrightarrow E$$

$$\omega \longmapsto X(\omega)$$

vérifiant

$$\forall k \in E \quad X^{-1}(\{k\}) \in \mathcal{F}$$

est appelée **variable aléatoire discrète**. L'ensemble $X(\Omega) \subset E$ est appelé **espace des états** de $X$.

En pratique, la condition $X^{-1}(\{k\}) \in \mathcal{F}$ n'est pas un obstacle : le plus souvent, on ne définit pas explicitement $\Omega$ et $\mathcal{F}$, et on suppose toujours que $\mathcal{F}$ est assez grande pour contenir tous les ensembles $X^{-1}(\{k\})$. L'ensemble $X^{-1}(\{k\})$ est alors un [[Évènement]], de sorte que sa probabilité est définie. On note le plus souvent cet évènement $[X = k]$ (ou $(X = k)$, ou $\{X = k\}$ suivant les auteurs) ; ces notations équivalentes signifient

$$\{\omega \in \Omega \mid X(\omega) = k\},$$

c'est-à-dire l'ensemble des expériences aléatoires $\omega$ pour lesquelles la valeur de la variable aléatoire $X$ est $k$.

Dans le cas d'une [[Variable aléatoire réelle|variable aléatoire réelle]], l'ensemble des valeurs prises $X(\Omega)$ est une partie de $\mathbb{R}$, et la définition prend la forme suivante.

Soit $X$ une v.a.r. telle que $X(\Omega)$ soit une partie finie ou dénombrable de $\mathbb{R}$. Alors la [[Loi d'une variable aléatoire|loi de probabilité]] $p_X$ de $X$ est une [[Probabilité discrète|loi de probabilité discrète]] sur $X(\Omega)$. On dit que $X$ est une **v.a. discrète portée par $X(\Omega)$**.

# Remarque

- Une variable aléatoire discrète est un cas particulier de [[Variable aléatoire]]. Pour une telle variable, c'est l'ensemble d'arrivée $X(\Omega)$ qui est **fini ou dénombrable** ; l'ensemble de départ $\Omega$ peut, lui, ne pas l'être. La [[Loi géométrique|v.a. géométrique]] en est un exemple : elle est définie sur $\Omega = \{0, 1\}^{\mathbb{N}^*}$, ensemble en bijection avec $\mathbb{R}$ donc non dénombrable, sans que cela l'empêche d'être une variable aléatoire discrète.
- Si $X$ est discrète, pour connaître sa loi de probabilité $p_X$, il suffit de connaître $p_X(\{k\}) = \mathbb{P}(X = k)$ pour tout $k \in X(\Omega)$.
- Dans un tel cas, la probabilité $p_X$ est définie sur la tribu $\mathcal{P}(X(\Omega))$, qui est incluse dans la [[Tribu borélienne|tribu borélienne]] $\mathcal{B}(\mathbb{R})$. Il est facile de prolonger $p_X$ à la tribu $\mathcal{B}(\mathbb{R})$ : voir [[Loi d'une variable aléatoire]] pour un exemple de prolongement d'une loi discrète.

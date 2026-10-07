# Définition

Il est immédiat d'étendre la définition de l'[[Espérance d'une variable aléatoire|espérance]] à une variable aléatoire $Z = Z_1 + iZ_2$ à valeurs complexes : il suffit pour cela que les [[Variable aléatoire réelle|variables aléatoires réelles]] $Z_1$ et $Z_2$ admettent une espérance, et on a alors

$$\mathbb{E}(Z) = \mathbb{E}(Z_1) + i\mathbb{E}(Z_2)$$

Toute variable aléatoire complexe bornée (c'est-à-dire telle qu'il existe $M > 0$ tel que $|Z| \leq M$) admet une espérance, puisque

$$\int_{\Omega} |Z_1(\omega)| d\mathbb{P}(\omega) \leq M \int_{\Omega} d\mathbb{P}(\omega) = M < \infty$$

(de même pour $|Z_2|$).

Soit $X$ une variable aléatoire réelle. Pour tout $\xi$ réel, la variable aléatoire complexe $e^{i\xi X}$ est de module 1, donc est bornée, donc admet une espérance. Cette espérance est une fonction de $\xi$ appelée **fonction caractéristique** de $X$.

Soient $(\Omega, \mathcal{F}, \mathbb{P})$ un [[Espace probabilisé|espace probabilisé]] et $X$ une variable aléatoire réelle définie sur $\Omega$. On appelle **fonction caractéristique** de $X$ la fonction $\Phi_X$ définie sur $\mathbb{R}$ par

$$\forall \xi \in \mathbb{R}\qquad \Phi_X(\xi)=\mathbb{E}\!\left(e^{i\xi X}\right)$$

# Propriétés

**Lien avec la transformée de Fourier.**

1. Si $X$ est [[Variable aléatoire continue|continue]], alors $\Phi_X$ est la transformée de Fourier de la [[Probabilité à densité|densité]] $f_X$ :

$$\Phi_X(\xi) = \int_{-\infty}^{+\infty} f_X(x)e^{i\xi x}\,dx$$

2. Si $X$ est [[Variable aléatoire discrète|discrète]] à valeurs dans $\mathbb{Z}$, alors $\Phi_X$ est la transformée de Fourier discrète de la suite $(p_X(\{k\}))_{k \in \mathbb{Z}}$, où $p_X$ est la [[Loi d'une variable aléatoire|loi de probabilité]] de $X$ :

$$\Phi_X(\xi) = \sum_{k \in \mathbb{Z}} e^{i\xi k} p_X(\{k\})$$

**Liens avec les moments de $X$.** Soit $X$ une variable aléatoire réelle admettant un [[Moment d'ordre k|moment d'ordre]] $n \geq 1$. Alors $\Phi_X$ est $n$ fois dérivable sur $\mathbb{R}$ et on a

$$\forall k \in \{0,1,\ldots,n\} \qquad \mathbb{E}(X^k)=(-i)^k\Phi_X^{(k)}(0)$$

Ce résultat est admis ; la formule se retrouve formellement en faisant un développement limité de l'exponentielle « sous le signe $\mathbb{E}$ ».

# Interprétation

**Utilisation.** Si, par un moyen ou un autre, on a obtenu $\Phi_X$ sans connaître $p_X$, à partir d'un catalogue de lois de probabilités, on peut comparer $\Phi_X$ aux fonctions caractéristiques de ces lois usuelles pour tenter de déterminer la loi de $X$ sans aucun calcul de probabilités (voir [[Caractérisation de la loi par la fonction caractéristique]]). La fonction caractéristique est donc un outil analytique d'étude des lois de probabilité, qui réduit certaines questions purement probabilistes à de simples calculs d'intégrales ou de sommes.

Cet outil est particulièrement adapté à la recherche de la loi d'une somme de variables aléatoires [[Indépendance de variables aléatoires|indépendantes]] : si $X$ et $Y$ sont indépendantes, si l'on connaît leurs lois (ou leurs fonctions caractéristiques), alors la fonction caractéristique de $X + Y$ est

$$\Phi_{X+Y}(\xi) = \Phi_X(\xi)\Phi_Y(\xi)$$

sans passer par la recherche de la loi de $X + Y$. Cela permet de trouver la loi de $X + Y$ (par lecture du catalogue, ou par transformation de Fourier inverse si l'on ne trouve pas $\Phi_X(\xi)\Phi_Y(\xi)$ dans le catalogue). La fonction caractéristique intervient également dans l'étude de la convergence en loi : voir [[Théorème de Paul Lévy]].

# Remarque

Si $X$ est à valeurs dans $\mathbb{N}$, alors elle a une [[Fonction génératrice|fonction génératrice]] :

$$G_X(z) = \mathbb{E}(z^X) = \sum_{n \in \mathbb{N}} z^n \mathbb{P}(X = n)$$

et une fonction caractéristique :

$$\Phi_X(\xi) = \mathbb{E}(e^{i\xi X}) = \sum_{n \in \mathbb{N}} e^{in\xi} \mathbb{P}(X = n)$$

Si le rayon de convergence de $G_X$ est $> 1$, on peut prendre $z = e^{i\xi}$ et on obtient la formule :

$$\Phi_X(\xi) = G_X\left(e^{i\xi}\right)$$

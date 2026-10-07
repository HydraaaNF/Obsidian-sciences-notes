# Définition

La notion de [[Fonction caractéristique|fonction caractéristique]] d'une variable aléatoire réelle se généralise immédiatement à des [[Vecteur aléatoire|vecteurs aléatoires]].

Soit $X$ un vecteur aléatoire de $\mathbb{R}^n$. Sa **fonction caractéristique** est définie pour $\xi \in \mathbb{R}^n$ par

$$\Phi_X(\xi) = \mathbb{E}(e^{iX \cdot \xi})$$

où $\mathbb{E}$ désigne l'[[Espérance d'une variable aléatoire|espérance]]. La notation $X \cdot \xi$ désigne le produit scalaire des vecteurs $X$ et $\xi$.

Cette définition convient pour tous vecteurs aléatoires de $\mathbb{R}^n$ et tous vecteurs $\xi$, car la v.a. complexe $e^{iX\cdot\xi}$ est bornée (son module vaut 1) donc intégrable.

# Propriétés

**Lien avec la transformée de Fourier.** Si $X$ est un vecteur aléatoire continu, sa fonction caractéristique est la transformée de Fourier $n$-dimensionnelle de la [[Loi d'un vecteur aléatoire|densité]] $f_X$, i.e.

$$\Phi_X(\xi) = \int_{\mathbb{R}^n} e^{ix \cdot \xi} f_X(x) \, dx$$

Ce résultat s'obtient par le [[Théorème de transfert pour un vecteur aléatoire|théorème de transfert]].

**Cas de coordonnées indépendantes.** La fonction caractéristique permet de déterminer facilement la [[Loi d'un vecteur aléatoire|loi conjointe]] lorsque les coordonnées sont indépendantes. Soit $X = (X_1, \dots, X_n)$ un vecteur aléatoire de $\mathbb{R}^n$ dont les coordonnées $X_i$ sont [[Indépendance des coordonnées d'un vecteur aléatoire|indépendantes]]. Alors

$$\forall \xi = (\xi_1, \dots, \xi_n) \in \mathbb{R}^n \qquad \Phi_X(\xi) = \Phi_{X_1}(\xi_1) \cdots \Phi_{X_n}(\xi_n)$$

### Démonstration

C'est immédiat. On a :

$$\Phi_X(\xi) = \mathbb{E}\left(e^{i \sum_{k=1}^n X_k \xi_k}\right) = \mathbb{E}\left(\prod_{k=1}^n e^{i X_k \xi_k}\right)$$

avec les v.a. complexes $e^{iX_k\xi_k}$ qui sont indépendantes, donc l'espérance de leur produit est le produit de leurs espérances.

La réciproque est admise : si la fonction caractéristique d'un vecteur aléatoire est le produit des fonctions caractéristiques des coordonnées, alors les coordonnées sont des variables aléatoires réelles [[Indépendance de variables aléatoires|indépendantes]].

**Cas d'une somme de variables aléatoires indépendantes.** La fonction caractéristique est un outil analytique puissant pour déterminer rapidement la loi d'une somme de v.a.r. indépendantes. Soit $X_1, \dots, X_n$ des v.a.r. [[Indépendance de variables aléatoires|indépendantes]], et soit $S = \sum_{i=1}^n X_i$. Alors

$$\forall \xi \in \mathbb{R} \quad \Phi_S(\xi) = \prod_{k=1}^n \Phi_{X_k}(\xi)$$

### Démonstration

C'est là aussi immédiat. On a

$$\Phi_S(\xi) = \mathbb{E}\left(e^{i\xi \sum_{k=1}^n X_k}\right) = \mathbb{E}\left(\prod_{k=1}^n e^{iX_k\xi}\right)$$

avec les v.a. complexes $e^{iX_k\xi}$ qui sont indépendantes.

**Densité de la somme de deux variables aléatoires indépendantes.** On en déduit immédiatement, puisque la transformée de Fourier d'un produit de convolution de deux fonctions de $L^1(\mathbb{R})$ est le produit des transformées de Fourier, le résultat suivant. Soit $X$ et $Y$ des v.a.r. [[Variable aléatoire continue|continues]] et [[Indépendance de variables aléatoires|indépendantes]]. Alors la v.a.r. $X + Y$ a pour densité

$$f_{X+Y} = f_X * f_Y$$

Cette formule est encore valable dans le cas où l'une des v.a. (disons $X$) prend un nombre fini de valeurs, à condition de remplacer la densité de $X$ par une combinaison linéaire de distributions de Dirac.

# Exemple

**Reconstitution d'un signal bruité en transmission numérique.**

On considère un canal transmettant dans l'idéal un 0 ou un 1 avec la même probabilité $1/2$. En pratique, un bruit de transmission gaussien centré d'écart-type $\sigma$, supposé indépendant du signal à transmettre, s'y ajoute. On note $X$ le signal à transmettre : $X$ est une [[Loi de Bernoulli|variable aléatoire de Bernoulli]] équidistribuée (en particulier, $X$ est discrète). On note $B$ le bruit de transmission, une [[Loi gaussienne|variable aléatoire gaussienne]] de loi $\mathcal{N}(0, \sigma^2)$, de densité

$$f_B(x) = \frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{x^2}{2\sigma^2}}$$

et $Y = X + B$ le signal bruité.

La v.a. $B$ prenant toute valeur réelle, $Y$ prend lui aussi toute valeur réelle, alors que le signal $X$ à reconstituer à partir de la valeur observée de $Y$ ne prend que les valeurs 0 et 1. Puisque $X$ et $B$ sont [[Indépendance de variables aléatoires|indépendantes]], la distribution de probabilité $p_{X+B}$ est le produit de convolution des distributions $p_X$ et $p_B$. Il est pratique d'utiliser un abus de langage se justifiant en se plaçant dans le cadre des distributions : la v.a. $X$ admet la « pseudo-densité »

$$\frac{1}{2}\delta(x) + \frac{1}{2}\delta(x-1)$$

où $\delta(x)$ et $\delta(x-1)$ désignent respectivement les distributions de Dirac $\delta_0$ et $\delta_1$, donc la v.a. $Y = X + B$ admet la pseudo-densité

$$f_Y = \left( \frac{1}{2}\delta_0 + \frac{1}{2}\delta_1 \right) * f_B$$

Il s'agit ici de convolution au sens des distributions. On utilise la distributivité de $*$ par rapport à $+$, puis le fait que convoluer par la masse de Dirac $\delta_a$ revient à translater de $a$. On obtient ainsi :

$$f_Y(x) = \frac{1}{2}f_B(x) + \frac{1}{2}f_B(x-1) = \frac{1}{2\sigma\sqrt{2\pi}} \left( e^{-\frac{x^2}{2\sigma^2}} + e^{-\frac{(x-1)^2}{2\sigma^2}} \right)$$

On remarque que $Y$ est une v.a. [[Variable aléatoire continue|continue]] (la pseudo-densité de $Y$ est une vraie densité), dont la densité est la somme d'une gaussienne centrée en 0 et d'une gaussienne centrée en 1. Lorsque $\sigma$ est petit, la fonction $f_Y$ présente des maxima en $x = 0$ et en $x = 1$. Dans ce cas, la probabilité que $Y$ tombe dans un petit intervalle centré sur 0 ou sur 1 est forte, de sorte qu'en pratique le signal bruité $Y$ permet de retrouver la valeur (0 ou 1) de $X$, ce qui est normal puisque dans ce cas le bruit $B$ est petit (localisé autour de 0). Par contre, lorsque $\sigma$ est grand, la fonction $f_Y$ présente un unique maximum en $x = 1/2$, de sorte qu'en pratique les valeurs de $Y$ tombent souvent près de $1/2$ et la valeur de $Y$ ne permet pas de faire une prédiction fiable sur la valeur de $X$ : le bruit est très dispersé et le signal est « perdu dans le bruit ».

# Remarque

Pour l'étude de la fonction caractéristique d'un [[Vecteur gaussien|vecteur gaussien]], voir [[Fonction caractéristique d'un vecteur gaussien]].

# Définition

Soit $D$ un sous-ensemble de $\mathbb{R}^2$ d'aire finie. L'aire de $D$ est le nombre

$$\mathcal{A}(D) = \iint_D dx\,dy$$

Un couple $(X, Y)$ de [[Variable aléatoire réelle|variables aléatoires réelles]] suit la **loi uniforme sur $D$** si sa [[Loi d'un vecteur aléatoire|loi conjointe]] admet la [[Probabilité à densité|densité]]

$$f_{(X,Y)}(x,y) = \frac{1}{\mathcal{A}(D)}\mathbf{1}_D(x,y)$$

De même, soit $D$ un sous-ensemble de $\mathbb{R}^3$ de volume fini. Le volume de $D$ est le nombre

$$\mathcal{V}(D) = \iiint_D dx\,dy\,dz$$

Un triplet $(X, Y, Z)$ suit la **loi uniforme sur $D$** s'il admet la densité

$$f_{(X,Y,Z)}(x, y, z) = \frac{1}{\mathcal{V}(D)} \mathbf{1}_D(x, y, z)$$

Plus généralement, pour une partie [[Tribu borélienne|mesurable]] $D$ de $\mathbb{R}^n$, on définit **l'hypervolume** de $D$ par $\int_D dx$. Cette quantité est soit $+\infty$, soit un nombre positif fini ; dans ce dernier cas, on applique à $D$ la construction précédente et la densité uniforme s'écrit, pour un [[Vecteur aléatoire|vecteur aléatoire]] $X = (X_1, \dots, X_n)$,

$$f_X(x) = \frac{1}{\int_D dx}\mathbf{1}_D(x)$$

# Propriétés

**Probabilité d'une partie.** Cela signifie que les valeurs prises par le couple $(X, Y)$ sont celles de $D$, et que la probabilité de tomber dans une partie $\Delta$ de $D$, c'est-à-dire $\mathbb{P}((X, Y) \in \Delta)$, est

$$\begin{aligned} \iint_{\Delta} \frac{1}{\mathcal{A}(D)} \mathbf{1}_D(x, y)\,dx\,dy &= \frac{1}{\mathcal{A}(D)} \iint_{\Delta} dx\,dy \\ &= \frac{\mathcal{A}(\Delta)}{\mathcal{A}(D)} \end{aligned}$$

C'est bien ce que l'on attend d'une loi uniforme sur $D$.

Pour un triplet $(X, Y, Z)$ uniforme sur un sous-ensemble $D$ de $\mathbb{R}^3$, les valeurs prises sont celles de $D$, et la probabilité de tomber dans une partie $\Delta$ de $D$ est

$$\begin{aligned} \iiint_{\Delta} \frac{1}{\mathcal{V}(D)} \mathbf{1}_D(x, y, z)\,dx\,dy\,dz &= \frac{1}{\mathcal{V}(D)} \iiint_{\Delta} dx\,dy\,dz \\ &= \frac{\mathcal{V}(\Delta)}{\mathcal{V}(D)} \end{aligned}$$

ce qui est bien, là aussi, ce que l'on attend d'une loi uniforme sur $D$.

# Liens avec d'autres lois

La loi uniforme sur un domaine **généralise** la [[Loi uniforme continue|loi uniforme continue]] : en dimension $n = 1$, un intervalle $D = [a, b]$ avec $b > a$ donne la densité

$$f_X(x) = \frac{1}{b-a} \mathbf{1}_{[a,b]}(x)$$

c'est-à-dire la loi uniforme sur $[a, b]$.

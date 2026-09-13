# Loi
## Cas discret
Une variable aléatoire $X$ suit la loi discrète uniforme sur $\{x_1, ..., x_n\}$ si l'ensemble $X(\Omega)$ des valeurs prises par $X$ est $\{x_1, ..., x_n\}$, et $$\forall j \in X(\Omega), \mathbb{P}(X = x_j) = \frac{1}{n}$$
## Cas continue
Soit $a$ et $b$ deux réels tels que $b > a$. Une variable aléatoire réelle $X$ suit la loi uniforme sur $\left[a, b\right]$ si elle admet la densité $$f_X(x) = \frac{1}{b-a}\mathbb{1}_{\left[a,b\right]}(x)$$
# Propriétés
## Cas discret
Soit $n$ un entier naturel non nul et soit $X \sim \mathcal{U}([\![1, n]\!])$, alors
- $\mathbb{E}(X) = \frac{n+1}{2}$
- $\mathbb{V}(X) = \frac{n^2 - 1}{12}$
- $G_X(z) = \frac{z(z^n-1)}{n(z-1)}$
## Cas continue
Soit $X \sim \mathcal{U}(\left[a, b\right])$, alors
- $\mathbb{E}(X) = \frac{a+b}{2}$
- $\mathbb{V}(X) = \frac{(a-b)^2}{12}$
- $\phi_X(\xi) = \frac{e^{ib\xi} - e^{ia\xi}}{i(b-a)\xi}$
- si $b > 0, a=-b$, on a $\phi_X(\xi) = \frac{sin(b\xi)}{b\xi}$

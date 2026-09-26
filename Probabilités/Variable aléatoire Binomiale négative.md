# Loi
Soit $r \in \mathbb{N}^*$ et $p \in \left]0, 1\right[$. $X \sim \mathcal{BN}(r, p)$ si $X(\Omega) = [\![ r, +\infty [\![$, avec $\mathbb{P}(X = k) = \binom{k - 1}{r - 1} p^r (1-p)^{k-r}$ pour tout $k \in \mathbb{N}$

# Interprétation
$X$ compte le nombre de tentatives avant l'obtention du $r^e$ succès, dans une répétition d'épreuves de Bernoulli indépendantes de paramètre $p$. Contrairement à la loi binomiale où le nombre d'épreuves est fixé à l'avance, c'est ici le nombre de succès visés $r$ qui est fixé, et le nombre d'épreuves qui est aléatoire.

Remarque : pour $r = 1$, $\mathcal{BN}(1, p)$ est la loi géométrique $\mathcal{G}(p)$ (nombre d'échecs avant le premier succès) : $\binom{k-1}{0} p (1-p)^{k-1} = p(1-p)^{k-1}$

# Propriétés
Soit $X \sim \mathcal{BN}(r, p)$, alors

* $\mathbb{E}(X) = \dfrac{r}{p}$
* $\mathbb{V}(X) = \dfrac{r(1-p)}{p^2}$
* $G_X(z) = \left( \dfrac{pz}{1 - (1-p)z} \right)^r, \quad |z| < \dfrac{1}{1-p}$

# Lien avec la loi binomiale
Si $Y \sim \mathcal{B}(k + r, p)$, alors $\mathbb{P}(X \leq k) = \mathbb{P}(Y \geq r)$ : ($X \leq k$ : le $r^e$ succès est venu au plus tard après $k^e$ échecs) ***équivalent à dire*** ($Y \geq r$ : il y a eu au moins $r$ succès parmi $k+r$ épreuves)
# Loi
Soit $\lambda > 0$. $X \sim \mathcal{E}(\lambda)$ si $X$ admet pour densité $f_X(x) = \lambda e^{-\lambda x}$ pour $x \geq 0$, et $f_X(x) = 0$ pour $x < 0$

Fonction de répartition : $F_X(x) = 1 - e^{-\lambda x}$ pour $x \geq 0$

# Interprétation
X modélise un temps d'attente avant un évènement (durée de vie sans usure, temps entre deux appels, désintégration radioactive). C'est le cas particulier $k=1$ de la [[Variable aléatoire de Weibull]] : le taux de risque instantané est constant, égal à $\lambda$.

Propriété d'absence de mémoire (caractéristique de l'exponentielle parmi les lois continues) :
$$\mathbb{P}(X > s+t \mid X > s) = \mathbb{P}(X > t), \qquad \forall s, t \geq 0$$

# Propriétés
Soit $X \sim \mathcal{E}(\lambda)$, alors

* $\mathbb{E}(X) = \dfrac{1}{\lambda}$
* $\mathbb{V}(X) = \dfrac{1}{\lambda^2}$
* $M_X(t) = \dfrac{\lambda}{\lambda - t}, \quad t < \lambda$
* $\varphi_X(t) = \dfrac{\lambda}{\lambda - it}$

# Liens avec d'autres lois
* Analogue continu de la [[Variable aléatoire géométrique]] (seule loi discrète à vérifier l'absence de mémoire)
* Cas particulier $n=1$ de la [[Variable aléatoire Erlang]] : $\mathcal{E}(\lambda) = \text{Erlang}(1, \lambda)$
* Une somme de $n$ variables $\mathcal{E}(\lambda)$ indépendantes suit une [[Variable aléatoire Erlang|loi d'Erlang]] $\text{Erlang}(n, \lambda)$
* Cas particulier de la [[Variable aléatoire gamma]] à paramètre de forme $1$
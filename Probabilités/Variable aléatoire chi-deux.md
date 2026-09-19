# Loi
Soit $n \in \mathbb{N}^*$. $X \sim \chi^2(n)$ (loi du chi-deux à $n$ degrés de liberté) si $X$ admet pour densité

$$f_X(x) = \frac{1}{2^{n/2} \, \Gamma(n/2)} \, x^{n/2 - 1} \, e^{-x/2}, \qquad x \geq 0$$

où $\Gamma$ est la [[Fonction Gamma]]

# Caractérisation
Soient $Z_1, \ldots, Z_n$ des variables i.i.d. $\sim \mathcal{N}(0,1)$. Alors

$$X = \sum_{i=1}^{n} Z_i^2 \; \sim \; \chi^2(n)$$

C'est la définition constructive usuelle de la loi, dont la densité ci-dessus se déduit.

# Interprétation
X mesure une somme de carrés d'écarts gaussiens centrés réduits indépendants. Utilisée massivement en statistique inférentielle :

* test d'adéquation (test du $\chi^2$)
* test d'indépendance sur tableau de contingence
* intervalle de confiance pour la variance d'un échantillon gaussien

# Propriétés
Soit $X \sim \chi^2(n)$, alors

* $\mathbb{E}(X) = n$
* $\mathbb{V}(X) = 2n$
* $M_X(t) = (1 - 2t)^{-n/2}, \quad t < \dfrac{1}{2}$
* $\varphi_X(t) = (1 - 2it)^{-n/2}$

# Liens avec d'autres lois
* Cas particulier de la [[Variable aléatoire gamma]] : $\chi^2(n) = \text{Gamma}(n/2, 2)$ (forme $n/2$, échelle $2$)
* Cas particulier $n=2$ : $\chi^2(2) \sim \mathcal{E}(1/2)$ — voir [[Variable aléatoire exponentielle]]
* Stabilité par somme : si $X_1 \sim \chi^2(n_1)$ et $X_2 \sim \chi^2(n_2)$ indépendantes, alors $X_1 + X_2 \sim \chi^2(n_1+n_2)$
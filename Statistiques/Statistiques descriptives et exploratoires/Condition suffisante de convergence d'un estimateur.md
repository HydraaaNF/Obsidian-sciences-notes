# Théorème

Soit $(X_n)_{n \geq 1}$ une suite de v.a. indépendantes et de même loi (i.i.d.) et

$$T_n = f(X_1, \dots, X_n)$$

un [[Estimateur|estimateur]] de $\theta$. Si pour tout $n \geq 1$, $T_n$ admet un [[Moment d'ordre k|moment d'ordre 2]] et

$$\mathbb{E}[T_n] \xrightarrow{n \rightarrow \infty} \theta$$

$$\mathbb{V}(T_n) \xrightarrow{n \rightarrow \infty} 0$$

alors $T_n$ est un [[Estimateur convergent|estimateur (faiblement) convergent]] de $\theta$.

# Remarque

Ce résultat est intuitivement évident. En effet, $T_n$ se rapproche en moyenne de $\theta$ (son [[Biais d'un estimateur|biais]] tend vers zéro) et sa dispersion devient négligeable quand $n$ grandit. Ce critère s'applique notamment à la [[Variance empirique]].

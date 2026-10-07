# Algorithme

Pour estimer la [[Variance|variance]] $\sigma^2$ d'une loi quelconque, il n'existe pas de méthode générale. Il faut donc, dans chaque cas, utiliser la procédure en quatre étapes de construction d'un [[Intervalle de confiance|intervalle de confiance]] pour un paramètre $\theta$, appliquée ici à $\theta = \sigma^2$ :

1. Introduire un [[Estimateur|estimateur]] $T$ de $\sigma^2$ dont la définition ne comporte pas de paramètre inconnu.
2. Construire une variable aléatoire $g(T)$ dépendant de $\sigma^2$ dont on sait déterminer la loi, exacte ou approchée, mais de préférence tabulée.
3. Déterminer $\lambda$ et $\mu$ tels que $\mathbb{P}\left[g(T) \in [\lambda; \mu]\right] = 1 - \alpha$.
4. En déduire $a(X_1, \dots, X_n)$ et $b(X_1, \dots, X_n)$ tels que

$$\mathbb{P}\left[a(X_1,\dots,X_n) \leq \sigma^2 \leq b(X_1,\dots,X_n)\right] = 1 - \alpha.$$

Dans ce cas, $a(X_1,\dots,X_n)$ et $b(X_1,\dots,X_n)$ doivent être des variables aléatoires *positives* pour que l'encadrement

$$a(x_1,\dots,x_n) \leq \sigma^2 \leq b(x_1,\dots,x_n)$$

présente un réel intérêt. Cet encadrement fournit alors l'intervalle de confiance au niveau $1 - \alpha$ pour $\sigma^2$.

La méthode s'illustre dans le cas gaussien, selon que l'espérance de la loi mère est connue ou inconnue.

**Cas d'une loi gaussienne d'espérance connue.** On souhaite estimer la variance $\sigma^2$ de la loi mère $X \sim \mathcal{N}(m,\sigma^2)$ lorsque $m$ est connu (cas peu fréquent en pratique).

1. L'espérance $m$ étant connue, on choisit l'[[Estimateur du maximum de vraisemblance|estimateur du maximum de vraisemblance]] de $\sigma^2$ :

$$\widehat{\sigma^2} = \frac{1}{n} \sum_{i=1}^n (X_i - m)^2.$$

Cet estimateur est en effet le meilleur dans ce contexte : il est [[Estimateur fortement convergent|fortement convergent]], [[Biais d'un estimateur|sans biais]] et précis au sens de la [[Distance en moyenne d'ordre p|distance en moyenne quadratique]] car [[Estimateur efficace|efficace]]. De plus, il satisfait à la contrainte de la procédure rappelée plus haut : aucun paramètre inconnu n'intervient dans la définition de $\widehat{\sigma^2}$.

2. Pour déterminer la loi d'une fonction de $\widehat{\sigma^2}$, on remarque que $\widehat{\sigma^2}$ est une somme de $n$ carrés de variables aléatoires [[Loi gaussienne|gaussiennes]] i.i.d., ce qui fait penser à la définition d'une variable du [[Loi du chi-deux|$\chi_n^2$]]. Il faut pour cela que les variables gaussiennes en question soient centrées réduites, d'où l'introduction de

$$\sum_{i=1}^n \left( \frac{X_i - m}{\sigma} \right)^2.$$

Cette variable aléatoire est la somme de $n$ carrés de variables $\mathcal{N}(0,1)$ indépendantes, donc sa loi est $\chi_n^2$. Or cette variable aléatoire est tout simplement

$$g\left(\widehat{\sigma^2}\right) = \frac{n\widehat{\sigma^2}}{\sigma^2}.$$

On dispose ainsi d'une fonction de $\widehat{\sigma^2}$ dont on connaît la loi, et cette loi $\chi_n^2$ est tabulée :

- pour les petites valeurs de $n$, on utilise la table du $\chi_n^2$ ;
- si $n$ est grand, on peut utiliser une approximation par $\mathcal{N}(n,2n)$ en vertu du [[Théorème de la limite centrale|théorème de la limite centrale]].

3. Il reste à déterminer dans la table du $\chi_n^2$ des valeurs $\lambda$ et $\mu$ (avec $0 < \lambda < \mu$) telles que

$$\mathbb{P}\left[\frac{n\widehat{\sigma^2}}{\sigma^2} \in [\lambda;\mu]\right] = 1-\alpha.$$

4. Ainsi l'intervalle de confiance pour $\sigma^2$ au niveau $1-\alpha$ est

$$\left[\frac{n\widehat{\sigma^2}_{obs}}{\mu}, \frac{n\widehat{\sigma^2}_{obs}}{\lambda}\right]$$

où, bien sûr,

$$n\widehat{\sigma^2}_{obs} = \sum_{i=1}^n (x_i - m)^2$$

est la valeur observée de $n\widehat{\sigma^2}$.

**Cas d'une loi gaussienne d'espérance inconnue.** L'estimateur $\widehat{\sigma^2}$ n'est plus utilisable pour estimer $\sigma^2$ si $m$ est inconnu. On utilise alors $S^2$ ou $S'^2$, ce qui revient au même d'après la [[Loi de la variance empirique corrigée|loi de la variance empirique corrigée]] :

$$g(S^2) = \frac{nS^2}{\sigma^2} = \frac{(n-1)S'^2}{\sigma^2} \sim \chi_{n-1}^2,$$

les $X_i$ étant i.i.d. et gaussiennes. Ici, $S^2$ est la [[Variance empirique|variance empirique]] et $S'^2$ la variance empirique corrigée :

$$S^2 = \frac{1}{n} \sum_{i=1}^n (X_i - \overline{X})^2$$

$$S'^2 = \frac{1}{n-1} \sum_{i=1}^n (X_i - \overline{X})^2,$$

où $\overline{X} = \frac{1}{n} \sum_{i=1}^n X_i$ est la [[Moyenne empirique|moyenne empirique]]. Il reste à déterminer $\lambda$ et $\mu$ dans la table du $\chi_{n-1}^2$ tels que

$$\mathbb{P}\left[\frac{nS^2}{\sigma^2} \in [\lambda;\mu]\right] = 1-\alpha.$$

On en déduit que l'intervalle de confiance au niveau $1-\alpha$ pour $\sigma^2$ est

$$\left[\frac{ns^2}{\mu}, \frac{ns^2}{\lambda}\right]$$

où $s^2$ est la valeur observée de $S^2$.

# Remarque

Les formules ci-dessus supposent une loi mère gaussienne : pour une loi quelconque, il n'existe pas de méthode générale d'estimation d'une variance par intervalle.

Les bornes des intervalles font intervenir les quantiles $\lambda$ et $\mu$ en ordre inversé : $\sigma^2$ figurant au dénominateur de $g$, la borne inférieure s'obtient avec $\mu$ et la borne supérieure avec $\lambda$.

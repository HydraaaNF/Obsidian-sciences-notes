# Définition

Soit un estimateur $T$ d'un paramètre $\theta$, obtenu à partir d'un ensemble d'échantillons $X_i$. Les qualités attendues d'un estimateur sont :

- la [[Estimateur convergent|convergence]] : $T \to \theta$ quand $n \to \infty$ ;
- la vitesse de convergence : certains estimateurs convergent plus rapidement que d'autres ;
- le risque : le risque est défini comme l'[[Erreur quadratique moyenne|erreur quadratique moyenne]]

$$\mathbb{E}_\theta\left[(T - \theta)^2\right] = \underbrace{(\mathbb{E}[T] - \theta)^2}_{\text{biais}} + \underbrace{\mathbb{V}[T]}_{\text{variance}}$$

c'est-à-dire la somme du carré du [[Biais d'un estimateur|biais]] et de la [[Variance|variance]] de l'estimateur.

# Interprétation

La [[Moyenne empirique|moyenne empirique]] $\overline{X}$, la [[Variance empirique|variance empirique]] $S^2$ et la [[Proportion empirique|proportion empirique]] $F$ sont respectivement des [[Estimateur|estimateurs]] de la moyenne, de la variance et de la probabilité discrète, puisqu'elles [[Convergence presque sûre|convergent presque sûrement]] vers la vraie quantité ($m$, $\sigma^2$ et $p_k$).

Mais d'autres estimateurs peuvent être utilisés pour une même quantité, par exemple pour la moyenne :

- la [[Moyenne tronquée|moyenne $\alpha$-tronquée]], où les $\alpha n$ valeurs les plus grandes et les plus petites sont écartées ;
- la [[Médiane empirique|valeur médiane]] ($\alpha = 50\%$) ;
- la moyenne des valeurs extrêmes, $(\max(X_i) + \min(X_i))/2$ ;
- un échantillon choisi aléatoirement ;
- une valeur constante, par exemple $0$.

D'où le besoin d'une mesure de qualité.

# Propriétés

Étant donné deux estimateurs non biaisés, le meilleur est celui de variance la plus petite.

# Remarque

Pour la démonstration de cette décomposition et un exemple, voir [[Erreur quadratique moyenne]].

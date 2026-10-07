# Algorithme

On dispose de l'observation $(x_1, \dots, x_n)$ de l'[[Échantillon et échantillonnage|échantillon]] $(X_1, \dots, X_n)$ issu d'une loi mère connue mis à part le paramètre $\theta$ que l'on cherche à estimer. Afin de déterminer un [[Estimateur|estimateur]] de $\theta$, on cherche l'[[Estimateur du maximum de vraisemblance|estimateur du maximum de vraisemblance]], noté $\hat{\theta}$ (voir la [[Méthode du maximum de vraisemblance]]). Pour cela, on cherche généralement à résoudre l'équation du maximum de vraisemblance suivante

$$\frac{\partial}{\partial \theta} \mathcal{L}(x_1, \dots, x_n; \theta) = 0$$

ou encore

$$\frac{\partial}{\partial \theta} \mathcal{L}\mathcal{L}(x_1, \dots, x_n; \theta) = 0$$

qui est généralement plus facile. Supposons que cette équation ait une seule solution $\theta(x_1, \dots, x_n)$ correspondant à un maximum de la [[Fonction de vraisemblance|vraisemblance]] (cette valeur est fonction de l'observation $(x_1, \dots, x_n)$) ; alors l'estimateur du maximum de vraisemblance est donné par

$$\hat{\theta} = \theta(X_1, \dots, X_n).$$

On étudie alors les qualités de cet estimateur $\hat{\theta}$ :

1. $\hat{\theta}$ est-il [[Estimateur convergent|convergent]] ? Supposons que oui.
2. Est-il [[Biais d'un estimateur|sans biais]] ? Supposons que oui.
3. On calcule la [[Variance|variance]] $\mathbb{V}(\hat{\theta})$ (si elle existe).
4. Si le domaine de définition de la loi mère ne dépend pas de $\theta$, on calcule la [[Théorème de Fréchet-Darmois-Cramér-Rao|borne de F.D.C.R.]] $V_0 = 1/I_n(\theta)$. Pour cela, on utilise l'[[Calcul de l'information de Fisher sous hypothèse de Cramér-Rao|identité de Cramér-Rao]]. Attention, il n'est pas garanti que l'[[Information de Fisher|information de Fisher]] $I_n(\theta)$ existe.
5. Si $\mathbb{V}(\hat{\theta}) = V_0$, alors $\hat{\theta}$ est un [[Estimateur efficace|estimateur efficace]] de $\theta$. On a alors le meilleur estimateur car il a toutes les bonnes qualités y compris une précision maximale (c'est-à-dire une variance minimale).

# Remarque

Il faut cependant bien noter que ceci est le programme idéal et qu'il peut s'arrêter à n'importe quelle étape non satisfaite.

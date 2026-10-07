# Théorème

Si le domaine de définition de $X$ ne dépend pas du paramètre $\theta$ (dite **hypothèse de Cramér-Rao**), alors la [[Information de Fisher|quantité d'information de Fisher]] apportée par un échantillon de taille $n$ s'écrit

$$I_n(\theta) = -\mathbb{E}\left[ \frac{\partial^2}{\partial \theta^2} \mathcal{L}\mathcal{L}(X_1, \dots, X_n; \theta) \right] \quad \text{si elle existe.}$$

où $X_1, \dots, X_n$ est un [[Échantillon et échantillonnage|échantillon]] de variable mère $X$ et $\mathcal{L}\mathcal{L}(X_1, \dots, X_n; \theta)$ sa [[Fonction de vraisemblance|log-vraisemblance]].

# Interprétation

Sous l'hypothèse de Cramér-Rao, le calcul de la [[Information de Fisher|quantité d'information de Fisher]] $I_n(\theta)$ se simplifie : dans la grande majorité des cas, on l'obtient par la dérivée seconde de la log-vraisemblance.

# Remarque

L'hypothèse de Cramér-Rao est également celle sous laquelle s'applique la borne inférieure de la [[Variance|variance]] des [[Biais d'un estimateur|estimateurs sans biais]], donnée par le [[Théorème de Fréchet-Darmois-Cramér-Rao]] ; les [[Biais d'un estimateur|estimateurs sans biais]] qui l'atteignent sont dits [[Estimateur efficace|efficaces]].

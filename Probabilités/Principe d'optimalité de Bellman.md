# Théorème

**Principe d'optimalité de Bellman.** Le meilleur chemin partiel aboutissant à l'état $(i,t)$ fait nécessairement partie du meilleur chemin qui passe par $(i,t)$.

# Interprétation

Un état $(i,t)$ d'un [[Treillis|treillis]] peut être atteint par plusieurs chemins partiels distincts : sur un treillis à quatre états et huit observations $o_1, \ldots, o_8$, plusieurs chemins partiels aboutissent au même état. Un chemin complet passant par $(i,t)$ se décompose en un chemin partiel aboutissant à $(i,t)$, suivi de la suite du chemin après cet état ; comme cette suite ne dépend pas de la façon dont $(i,t)$ a été atteint, le meilleur chemin complet passant par $(i,t)$ contient nécessairement le meilleur des chemins partiels qui aboutissent à $(i,t)$.

Il suffit donc, à chaque état, de conserver le meilleur chemin partiel pour construire de proche en proche le meilleur chemin complet, sans énumérer tous les chemins possibles.

# Remarque

Le principe d'optimalité de Bellman est le fondement de l'[[Algorithme de Viterbi]], qui résout le [[Décodage d'une séquence d'états|décodage d'une séquence d'états]] d'un [[Modèle de Markov caché]].

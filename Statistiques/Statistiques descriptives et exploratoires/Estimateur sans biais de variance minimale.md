# Définition

Pour une famille de lois $f(x, \theta)$ donnée, un **estimateur sans biais de variance minimale** de $\theta$ est un [[Estimateur|estimateur]] [[Biais d'un estimateur|sans biais]] de $\theta$ dont la variance est minimale parmi tous les estimateurs sans biais de $\theta$.

# Remarque

La recherche du meilleur estimateur possible ne peut pas être menée en toute généralité ; il faut donc restreindre le problème :

- on se limite à une classe d'[[Estimateur|estimateurs]] ;
- on ne sait toujours pas résoudre le problème de minimisation du [[Risque généralisé|risque]] dans la plupart des cas.

La démarche consiste alors à chercher, pour une famille de lois $f(x, \theta)$ donnée, l'estimateur sans biais de $\theta$ de variance minimale. Cette recherche est reliée à la notion de [[Statistique suffisante|statistique suffisante]] ; le [[Théorème de Lehmann-Scheffé]] précise l'existence et l'unicité d'un tel estimateur.

Un [[Estimateur efficace]] est un cas particulier d'estimateur sans biais de variance minimale : sa variance atteint la [[Théorème de Fréchet-Darmois-Cramér-Rao|borne de Fréchet-Darmois-Cramér-Rao]].

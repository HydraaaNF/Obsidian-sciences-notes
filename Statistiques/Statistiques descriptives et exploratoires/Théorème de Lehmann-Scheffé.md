# Théorème

Si $T^*$ est un [[Estimateur|estimateur]] [[Biais d'un estimateur|sans biais]] de $\theta$ fonction d'une [[Statistique suffisante|statistique suffisante]] complète $U$, alors $T^*$ est l'unique [[Estimateur sans biais de variance minimale|estimateur sans biais de variance minimale]] de $\theta$. En particulier, si $T$ est un estimateur sans biais de $\theta$, alors $T^* = \mathbb{E}[T \mid U]$.

# Interprétation

Autrement dit, un estimateur sans biais fonction d'une statistique suffisante complète est le meilleur estimateur possible.

# Remarque

Le cas particulier $T^* = \mathbb{E}[T \mid U]$ est la construction du [[Théorème de Rao-Blackwell]] : conditionner un estimateur sans biais par une statistique suffisante donne un estimateur sans biais au moins aussi bon.

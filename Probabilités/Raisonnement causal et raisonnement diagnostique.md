#adm-7

# Interprétation

La factorisation d'une loi sur un graphe orienté acyclique, c'est-à-dire dans un [[Réseau bayésien]], autorise deux directions de raisonnement, selon le sens dans lequel le conditionnement traverse les flèches.

- Raisonnement **ascendant**, ou diagnostique : une conséquence est observée, on cherche la cause la plus probable.
- Raisonnement **descendant**, ou causal : une cause est donnée, on calcule la probabilité d'un évènement qui en dépend.

Les deux directions portent sur la même loi jointe et sur le même graphe : seule change la variable placée à droite du conditionnement.

### Raisonnement diagnostique

Sur le [[Réseau bayésien du système d'arrosage|système d'arrosage]], l'herbe mouillée $W$ est une conséquence et l'arroseur $S$ comme la pluie $R$ en sont les causes directes. Partant de l'observation $W = 1$, les deux questions diagnostiques sont

- $\mathbb{P}[S = 1 \mid W = 1]$ : l'arroseur a-t-il fonctionné, sachant l'herbe mouillée ?
- $\mathbb{P}[R = 1 \mid W = 1]$ : a-t-il plu, sachant l'herbe mouillée ?

Le conditionnement remonte les arcs $S \to W$ et $R \to W$ à contresens, de l'effet vers les causes. Ce retournement est l'office de la [[Formule de Bayes]] : elle exprime une probabilité conditionnelle effet vers cause à partir des probabilités conditionnelles cause vers effet, celles que portent les tables du modèle, et de la loi des causes. Le dénominateur, la probabilité de l'observation, renormalise le résultat.

### Raisonnement causal

Le raisonnement **descendant** suit les flèches. La cause racine du graphe est le temps nuageux $C$ ; une fois $C = 1$ connu, la probabilité de l'herbe mouillée s'écrit

$$\mathbb{P}[W = 1 \mid C = 1]$$

Aucune inversion n'est nécessaire : la probabilité se propage de $C$ vers $S$ et vers $R$, puis vers $W$, en sommant sur les variables intermédiaires non observées, et chaque facteur conditionnel se lit dans le sens de son arc.

# Remarque

Les deux raisonnements ne s'opposent pas : ils portent sur la même loi jointe et sur les mêmes tables conditionnelles, seule la question posée change. Le sens causal lit les facteurs dans l'ordre des arcs ; le sens diagnostique doit les inverser par la [[Formule de Bayes|formule de Bayes]].

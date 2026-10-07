# Théorème

Si les $B_i$ forment un [[Système complet d'évènements|système complet d'évènements]], alors, pour tout [[Évènement|évènement]] $A$ :

$$\mathbb{P}[A] = \sum_i \mathbb{P}[A \cap B_i]$$

En utilisant la [[Probabilités composées|règle de multiplication]] $\mathbb{P}[A \cap B_i] = \mathbb{P}[A \mid B_i]\mathbb{P}[B_i]$, où $\mathbb{P}[A \mid B_i]$ est la [[Probabilité conditionnelle|probabilité conditionnelle]] de $A$ sachant $B_i$, la formule prend la forme équivalente :

$$\mathbb{P}[A] = \sum_i \mathbb{P}[A \mid B_i]\mathbb{P}[B_i]$$

# Interprétation

La formule décompose le calcul de $\mathbb{P}[A]$ selon un système complet d'évènements : on additionne les contributions $\mathbb{P}[A \cap B_i]$ de tous les cas possibles, qui forment une partition de $\Omega$. Sous sa forme conditionnelle, $\mathbb{P}[A]$ est la somme des probabilités conditionnelles $\mathbb{P}[A \mid B_i]$, pondérées par les probabilités $\mathbb{P}[B_i]$ des cas.

# Remarque

La [[Formule de Bayes|formule de Bayes]] reprend la formule des probabilités totales au dénominateur : elle exprime $\mathbb{P}[B_j \mid A]$ à partir des probabilités conditionnelles $\mathbb{P}[A \mid B_i]$ et des probabilités $\mathbb{P}[B_i]$.

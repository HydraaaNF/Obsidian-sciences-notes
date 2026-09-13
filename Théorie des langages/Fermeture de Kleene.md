## Définition
Soit $L$ un [[Langage|langage]]. La fermeture de Kleene est d'un langage $L$ est définit par $L^* = \bigcup_{i \geq 0} L^i$. $L^*$ contient tous les mots qu'il est possible de construire en concaténant un nombre fini d'éléments du langage $L$. On définit également $L^+ = \bigcup_{i > 0} L^i = LL^*$.

## Remarques
- $\Sigma^*$ représente l'ensemble des séquences finies construites en concaténant des symboles de $\Sigma$, avec $\Sigma$ un alphabet.
- $\emptyset^*$ n'est pas vide, il contient $\epsilon$.
- $L^+$ contient $\epsilon$ seulement si $L$ le contient tandis que $L^*$ contient toujours $\epsilon$.
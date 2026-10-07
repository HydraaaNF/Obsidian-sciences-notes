# Définition

Soit $E$ un ensemble. On appelle ensemble des parties de $E$, noté $\mathcal{P}(E)$, l'ensemble dont les éléments sont les sous-ensembles de $E$.

# Propriétés

Soit $E$ un ensemble fini. Le nombre de parties de $E$ est

$$\text{card}(\mathcal{P}(E)) = 2^{\text{card}(E)}$$

où $\mathcal{P}(E)$ désigne l'ensemble des parties de $E$. En particulier, si $E$ comporte $n$ éléments, il existe $2^n$ parties de $E$.

# Remarque

- Dans un contexte probabiliste où $\Omega$ est fini ou dénombrable, on prend pour ensemble des évènements $\mathcal{P}(\Omega)$ tout entier : toute partie de $\Omega$ est alors un évènement (voir [[Tribu]]).
- Une partie de $E$ est déterminée par sa fonction indicatrice, c'est-à-dire par l'application de $E$ dans $\{0, 1\}$ qui vaut $1$ sur les éléments de la partie et $0$ ailleurs. Compter les parties de $E$ revient donc à compter les applications de $E$ dans $\{0, 1\}$ : voir [[Nombre d'applications entre ensembles finis]].

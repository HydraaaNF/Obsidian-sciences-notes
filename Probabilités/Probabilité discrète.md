# Définition

Soient $\Omega = \{x_n \mid n \in I\}$ un ensemble **fini ou dénombrable** ($I \subset \mathbb{N}$) et $(p_n)_{n \in I}$ une suite de réels **positifs** telle que

$$\sum_{n \in I} p_n = 1.$$

On définit une probabilité $\mathbb{P}$ (dite **discrète**) sur $\mathcal{P}(\Omega)$ de la façon suivante :

$$\forall A \in \mathcal{P}(\Omega) \quad \mathbb{P}(A) = \sum_{\{n \in I \mid x_n \in A\}} p_n.$$

Cette probabilité est appelée *loi de probabilité discrète sur $\Omega$*. On considère $p_n$ comme la probabilité de l'évènement élémentaire $\{x_n\}$ : un évènement est dit *élémentaire* lorsqu'il est réduit à une seule des éventualités possibles de l'expérience aléatoire considérée.

# Propriétés

- $\mathbb{P}(\{x_n\}) = p_n$ pour tout $n \in I$ ; en particulier, $p_n \in [0, 1]$.
- La probabilité d'un évènement quelconque $A \subset \Omega$ s'obtient en sommant les probabilités des éventualités appartenant à $A$ : la propriété de $\sigma$-additivité est vérifiée *par construction*.
- On a bien

$$\mathbb{P}(\Omega) = \sum_{\{n \in I \mid x_n \in \Omega\}} p_n = \sum_{n \in I} p_n = 1.$$

# Remarque

- La probabilité est définie sur $\mathcal{P}(\Omega)$ tout entier : toute partie de $\Omega$ est un évènement. Le triplet $(\Omega, \mathcal{P}(\Omega), \mathbb{P})$ est donc un [[Espace probabilisé]] dont l'univers est fini ou dénombrable.
- Lorsque les éventualités sont équiprobables, la loi s'appelle [[Loi uniforme discrète|loi discrète uniforme]].
- La construction s'applique en particulier à la [[Loi de Poisson]], définie sur $\Omega = \mathbb{N}$.

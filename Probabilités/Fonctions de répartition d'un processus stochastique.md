# Définition

Soit $X(t)$ l'« état » d'un [[Processus stochastique|processus stochastique]] au temps $t$.

La **fonction de répartition du premier ordre** est définie par

$$F(x; t) = \mathbb{P}[X(t) \leq x].$$

La **fonction de répartition du deuxième ordre** est définie par

$$F(x, x'; t, t') = \mathbb{P}[X(t) \leq x, X(t') \leq x'].$$

Plus généralement, la **fonction de répartition d'ordre $n$** est définie par

$$F(\mathbf{x}; \mathbf{t}) = \mathbb{P}[X(\mathbf{t}_1) \leq \mathbf{x}_1, \ldots, X(\mathbf{t}_n) \leq \mathbf{x}_n].$$

# Remarque

- La fonction de répartition du premier ordre $F(x; t)$ est la [[Fonction de répartition]] de la variable $X(t)$ : les fonctions de répartition d'un processus généralisent cette notion aux valeurs prises par le processus en plusieurs instants.
- La fonction de répartition du deuxième ordre fait intervenir la loi jointe du couple $(X(t), X(t'))$ ; celle d'ordre $n$ décrit la [[Loi d'un vecteur aléatoire|loi du vecteur aléatoire]] $(X(t_1), \ldots, X(t_n))$.

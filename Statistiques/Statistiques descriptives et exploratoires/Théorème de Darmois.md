# Théorème

Une condition nécessaire et suffisante pour qu'un [[Échantillon et échantillonnage|échantillon]] $(X_1, \dots, X_n)$ admette une [[Statistique suffisante]] est que la [[Probabilité à densité|densité]] appartienne à la famille exponentielle, c'est-à-dire

$$f(\mathbf{x}, \theta) = \exp(a(x)\alpha(\theta) + b(x) + \beta(\theta))$$

Sous certaines conditions sur la fonction $a$, la statistique $T = \sum a(X_i)$ est suffisante.

# Remarque

- Le théorème ne s'applique que si le domaine de définition de $X$ ne dépend pas de $\theta$.
- Il n'existe d'[[Estimateur efficace|estimateurs efficaces]] (c'est-à-dire sans biais de variance minimale) que pour la famille exponentielle.
- La plupart des lois usuelles, comme la [[Loi gamma]], appartiennent à la famille exponentielle ; font exception celles qui comportent un terme de la forme $x^\theta$.

Le [[Théorème de factorisation de Fisher]] fournit un critère de factorisation de la vraisemblance pour reconnaître une statistique suffisante.

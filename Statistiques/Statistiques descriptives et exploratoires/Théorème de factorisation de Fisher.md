# Théorème

Soient $X_1, \dots, X_n$ un [[Échantillon et échantillonnage|échantillon]] et $T$ une [[Statistique|statistique]]. On note

- $L(x_1, \dots, x_n; \theta)$ la densité ou fonction de masse de $(X_1, \dots, X_n)$, la [[Fonction de vraisemblance|vraisemblance]] ;
- $g(t; \theta)$ la densité ou fonction de masse de $T$.

$T$ est une [[Statistique suffisante|statistique suffisante]] si

$$L(\mathbf{x}, \theta) = g(t, \theta)h(\mathbf{x}),$$

ou, autrement dit, si la densité de $\mathbf{x}$ conditionnellement à $T$ est indépendante de $\theta$.

# Interprétation

L'idée est la suivante : si, lorsque $T$ est connu, la densité conditionnelle de $(X_1, \dots, X_n)$ ne dépend plus de $\theta$, alors $T$ porte toute l'information concernant $\theta$.

# Définition

Soit $X$ une [[Variable aléatoire continue|variable aléatoire continue]] définie sur un [[Espace probabilisé]], de densité de probabilité $f$ et de [[Fonction de répartition|fonction de répartition]] $F$. La densité est une fonction positive ou nulle et d'intégrale $1$ sur $\mathbb{R}$ :

$$f \geq 0$$

$$\int_{-\infty}^{+\infty} f(x)\,dx = 1.$$

Pour tout ensemble $A$ de la [[Tribu borélienne|tribu borélienne]] de $\mathbb{R}$, la probabilité que $X$ appartienne à $A$ s'obtient en intégrant la densité sur $A$ :

$$\mathbb{P}(X \in A) = \int_A f(x)\,dx.$$

# Propriétés

- Le **support** (ou *range*) de $X$ est l'ensemble des valeurs possibles pour $X$.
- La densité est la dérivée de la [[Fonction de répartition]] :

$$f(x) = \lim_{\delta \to 0^+} \frac{\mathbb{P}(x < X < x + \delta)}{\delta} = \lim_{\delta \to 0^+} \frac{F(x + \delta) - F(x)}{\delta} = F'(x).$$

# Remarque

- La densité est positive ou nulle : l'écriture $f > 0$ est une erreur fréquente, car une densité peut s'annuler, par exemple en dehors du support de $X$.
- L'écriture $f(x) = \lim_{\delta \to 0^+} \mathbb{P}(x < X < x + \delta)$ est une erreur fréquente : cette limite vaut $0$. C'est son taux d'accroissement, $\frac{\mathbb{P}(x < X < x + \delta)}{\delta}$, qui converge vers la densité $f(x) = F'(x)$.

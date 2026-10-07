# Théorème

Soit une [[Population statistique et caractère|population]] $\mathcal{P}$ de $n$ individus composée de $l$ sous-populations $\mathcal{P}_1, \ldots, \mathcal{P}_l$ d'effectifs $N_1, \ldots, N_l$ respectivement. On observe un caractère $X$ sur chacune de ces sous-populations, avec pour moyenne arithmétique $\bar{x}_j$ et variance $s_j^2$ pour $\mathcal{P}_j$. La [[Moyenne, médiane et mode|moyenne arithmétique]] et la [[Variance et écart-type|variance]] des observations sur la population totale $\mathcal{P}$ sont données par

$$\bar{x} = \frac{1}{n} \sum_{j=1}^l N_j \bar{x}_j$$

$$\begin{aligned} s^2 &= \frac{1}{n} \sum_{j=1}^l N_j s_j^2 + \frac{1}{n} \sum_{j=1}^l N_j (\bar{x}_j - \bar{x})^2 \\ &= \text{moyenne des variances} + \text{variance des moyennes.} \end{aligned}$$

### Démonstration

Notons les observations du caractère $X$ sur la sous-population $\mathcal{P}_j$ de la façon suivante

$$x_1^j, \dots, x_{N_j}^j.$$

On dispose ainsi de $n$ observations sur la population totale, c'est-à-dire

$$x_1^1, \dots, x_{N_1}^1, \dots, x_1^j, \dots, x_{N_j}^j, \dots, x_1^l, \dots, x_{N_l}^l$$

dont la moyenne est calculée par

$$\begin{aligned} \bar{x} &= \frac{1}{n} \left[ (x_1^1 + \dots + x_{N_1}^1) + \dots + (x_1^j + \dots + x_{N_j}^j) + \dots + (x_1^l + \dots + x_{N_l}^l) \right] \\ &= \frac{1}{n} \sum_{j=1}^l (x_1^j + \dots + x_{N_j}^j) \\ &= \frac{1}{n} \sum_{j=1}^l N_j \frac{x_1^j + \dots + x_{N_j}^j}{N_j} \\ &= \frac{1}{n} \sum_{j=1}^l N_j \bar{x}_j. \end{aligned}$$

En ce qui concerne la variance sur la population totale, on a

$$\begin{aligned} s^2 &= \frac{1}{n} \sum_{j=1}^l \sum_{i=1}^{N_j} \left( x_i^j - \bar{x} \right)^2 \\ &= \frac{1}{n} \sum_{j=1}^l N_j \left( s_j^2 + (\bar{x} - \bar{x}_j)^2 \right) \quad (\text{centrage pour la moyenne avec } a = \bar{x}) \\ &= \frac{1}{n} \sum_{j=1}^l N_j s_j^2 + \frac{1}{n} \sum_{j=1}^l N_j (\bar{x} - \bar{x}_j)^2 \end{aligned}$$

# Interprétation

La variance de la population totale se décompose en deux contributions :
- la **moyenne des variances** $\frac{1}{n} \sum_{j=1}^l N_j s_j^2$, dispersion à l'intérieur des sous-populations ;
- la **variance des moyennes** $\frac{1}{n} \sum_{j=1}^l N_j (\bar{x}_j - \bar{x})^2$, dispersion des moyennes des sous-populations autour de la moyenne globale.

La dispersion totale provient donc à la fois de l'hétérogénéité interne à chaque sous-population et des écarts entre les sous-populations.

# Remarque

La démonstration applique le [[Théorème de König-Huygens|centrage pour la moyenne]] à chaque sous-population, avec pour paramètre de centrage la moyenne de la population totale : $a = \bar{x}$, et non $a = \bar{x}_j$. C'est ce choix qui fait apparaître le terme $(\bar{x} - \bar{x}_j)^2$, donc la variance des moyennes ; avec $a = \bar{x}_j$, le centrage ne restitue que la variance $s_j^2$ de la sous-population.

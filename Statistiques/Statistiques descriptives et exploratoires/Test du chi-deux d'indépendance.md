# Définition
Pour une [[Table de contingence]] d'effectifs observés $n_{ij}$, la statistique du test est
$$\chi^2 = \sum_{i}\sum_{j} \frac{\left(n_{ij} - \frac{n_{i\cdot}n_{\cdot j}}{n}\right)^2}{\frac{n_{i\cdot}n_{\cdot j}}{n}}$$

# Interprétation
Mesure l'écart global entre les effectifs observés et ceux attendus sous [[Indépendance empirique|indépendance]]. Plus $\chi^2$ est grand, plus l'hypothèse d'indépendance entre $X$ et $Y$ est mise en doute.

# Exemple
Sur la [[Table de contingence|table de contingence]] latéralité × sexe (100 personnes), les effectifs théoriques sous indépendance sont $n_{ij} = \frac{n_{i\cdot}n_{\cdot j}}{n}$ :

| | Droitier (théorique) | Gaucher (théorique) |
|---|---|---|
| Homme | 45,24 | 6,76 |
| Femme | 41,76 | 6,24 |

$$\chi^2 = \frac{(43-45{,}24)^2}{45{,}24} + \frac{(9-6{,}76)^2}{6{,}76} + \frac{(44-41{,}76)^2}{41{,}76} + \frac{(4-6{,}24)^2}{6{,}24} \approx 1{,}78$$

# Remarque
Le cours ne donne que le tableau brut ; le calcul du $\chi^2$ ci-dessus n'est pas dans les diapositives, il est ajouté ici pour rendre l'exemple exploitable de bout en bout.

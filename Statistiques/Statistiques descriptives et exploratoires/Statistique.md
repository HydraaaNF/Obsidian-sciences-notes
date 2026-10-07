# Définition

Chaque [[Échantillon et échantillonnage|échantillon]] peut être vu comme une [[Variable aléatoire|variable aléatoire]] $X_i$, dont la valeur observée est $x_i$ ; toutes les variables $X_i$ suivent la même loi.

Une **statistique** est une variable aléatoire qui est une fonction mesurable de $X_1, X_2, \ldots, X_n$, notée

$$T = f(X_1, X_2, \ldots, X_n).$$

Quelques statistiques usuelles sur un ensemble d'observations $X_1, \ldots, X_n$ :

- la [[Proportion empirique|fréquence empirique]] :
  $$F_k = \frac{1}{n} \sum_{i=1}^n \delta(X_i = k)$$
- la [[Moyenne empirique|moyenne empirique]] :
  $$\overline{X} = \frac{1}{n} \sum_{i=1}^n X_i$$
- la [[Variance empirique|variance empirique]] :
  $$S^2 = \frac{1}{n} \sum_{i=1}^n (X_i - \overline{X})^2$$

# Exemple

Supposons que l'on extraie $n$ ampoules d'une chaîne de production et que l'on mesure leur durée de vie $x_i$. Si le procédé de fabrication n'a pas changé, les valeurs $x_i$ peuvent être considérées comme les observations d'une même variable aléatoire $X$. Le modèle considère $X_i$ comme la variable aléatoire correspondant à la durée de vie de la $i$-ème ampoule, dont la valeur observée est $x_i$. Toutes les variables $X_i$ suivent la même loi, celle de $X$.

# Propriétés

Une statistique est une variable aléatoire, puisque toute fonction de variables aléatoires est une variable aléatoire.

# Remarque

Un [[Estimateur]] est une statistique : c'est une fonction mesurable de l'échantillon $(X_1, \ldots, X_n)$.

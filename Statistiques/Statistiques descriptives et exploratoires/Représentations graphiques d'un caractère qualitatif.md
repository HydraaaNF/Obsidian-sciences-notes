# Définition

Pour visualiser les fréquences empiriques d'un [[Caractère qualitatif|caractère qualitatif]] à $k$ modalités, on dispose de deux représentations graphiques usuelles :

- le **diagramme en barres** (ou diagramme en bâtons) : une barre par modalité, de hauteur proportionnelle à l'effectif (ou à la fréquence) de la modalité ;
- le **diagramme circulaire**, aussi appelé **camembert** : un secteur par modalité, d'angle proportionnel à la fréquence de la modalité.

Pour la modalité $j$, d'effectif $n_j$ parmi $n$ [[Population statistique et caractère|individus]] observés, de fréquence

$$f_j = \frac{n_j}{n},$$

l'angle du secteur correspondant vaut

$$\theta_j = 2\pi f_j,$$

soit $360\,f_j$ degrés.

# Exemple

Un caractère qualitatif à trois modalités, numérotées 1, 2 et 3, représenté par un diagramme en barres des effectifs, puis par le diagramme circulaire des mêmes données :

```chart
type: bar
labels: ["1", "2", "3"]
series:
  - title: Effectif
    data: [11, 11, 12]
```

```chart
type: pie
labels: ["1", "2", "3"]
series:
  - title: Effectif
    data: [11, 11, 12]
```

valeurs relevées sur la figure, approximatives.

# Remarque

Pour un [[Caractère quantitatif discret|caractère quantitatif discret]], les fréquences empiriques se lisent sur la distribution empirique :

```chart
type: bar
labels: ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "10", "11"]
series:
  - title: Fréquence
    data: [0.006, 0.033, 0.083, 0.139, 0.176, 0.175, 0.145, 0.103, 0.064, 0.035, 0.018, 0.007]
```

valeurs relevées sur la figure, approximatives. Pour la construction détaillée (tableaux d'effectifs, de fréquences et diagrammes associés), voir [[Représentations graphiques d'un caractère quantitatif discret]].

Lorsque les modalités sont nombreuses, les trier par effectif décroissant met en évidence les plus fréquentes : c'est le principe du [[Diagramme de Pareto]].

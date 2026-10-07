# Définition

L'**éboulis des valeurs propres** (en anglais *scree plot*) est la représentation graphique des valeurs propres d'une [[Analyse en composantes principales]] en fonction de leur rang : chaque valeur propre est reportée selon la dimension qu'elle décrit, dans l'ordre décroissant.

# Exemple

Pour une analyse à dix dimensions, le pourcentage de variance expliquée par chaque dimension se lit sur un diagramme en barres :

```chart
type: bar
labels: ["1", "2", "3", "4", "5", "6", "7", "8", "9", "10"]
series:
  - title: Variance expliquée (en %)
    data: [41.2, 18.4, 12.4, 8.2, 7, 4.2, 3, 2.7, 1.6, 1.2]
```

Valeurs relevées sur la figure, approximatives. La décroissance est forte entre la première dimension (41,2 %) et la deuxième (18,4 %), puis s'atténue progressivement jusqu'à la dixième dimension (1,2 %).

# Remarque

L'éboulis des valeurs propres s'utilise dans le cadre de l'[[Analyse en composantes principales]] ; les mesures d'évaluation de la qualité de la représentation obtenue sont regroupées dans la [[Qualité d'une analyse en composantes principales]].

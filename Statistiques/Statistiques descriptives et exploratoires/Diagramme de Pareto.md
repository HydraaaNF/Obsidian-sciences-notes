# Définition

Le diagramme de Pareto est une représentation graphique destinée à mettre en évidence les facteurs les plus importants d'un phénomène : par exemple la principale source de défauts ou les motifs de réclamation les plus fréquents.

Comme le [[Représentations graphiques d'un caractère qualitatif|diagramme en barres]], il représente les effectifs d'un [[Caractère qualitatif|caractère qualitatif]] (causes, catégories) ; ses barres sont rangées par effectif décroissant et une courbe des pourcentages cumulés vient compléter le diagramme.

Il repose sur l'idée que 20 % des causes génèrent 80 % du résultat.

# Exemple

Retards par cause déclarée : les causes sont rangées par effectif décroissant et la courbe donne les pourcentages cumulés.

```chart
type: bar
labels: ["Trafic", "Garde d'enfants", "Transports en commun", "Météo", "Réveil tardif", "Urgence"]
series:
  - title: Effectif
    data: [57, 45, 28, 20, 12, 6]
  - title: Pourcentage cumulé
    data: [33.9, 60.7, 77.4, 89.3, 96.4, 100]
    type: line
```

valeurs relevées sur la figure, approximatives.

Deux causes sur six expliquent plus de 60 % des retards, trois sur six plus de 77 %.

Autre exemple, sous forme d'un simple diagramme en barres trié avec courbe cumulée :

```chart
type: bar
labels: ["Défaut A", "Défaut B", "Défaut C", "Défaut D", "Défaut E"]
series:
  - title: Effectif
    data: [45, 25, 15, 10, 5]
  - title: Fréquence cumulée (%)
    type: line
    data: [45, 70, 85, 95, 100]
```

# Remarque

Le [[Diagramme tiges et feuilles]] est une autre représentation d'une distribution empirique. Pour les représentations usuelles d'un caractère qualitatif sans tri par importance, voir [[Représentations graphiques d'un caractère qualitatif]].

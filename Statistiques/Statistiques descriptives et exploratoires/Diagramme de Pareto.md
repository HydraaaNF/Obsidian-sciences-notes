# Définition
Diagramme en barres où les catégories sont triées par fréquence décroissante, complété par la courbe des fréquences cumulées.

# Interprétation
Met en évidence les facteurs les plus importants (ex : principale source de défauts, motifs les plus fréquents de réclamation client).

# Remarque
Connu sous le nom de règle des 20/80 : environ 20 % des causes génèrent environ 80 % des effets.

# Exemple
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

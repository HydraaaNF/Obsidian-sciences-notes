# Définition
Représentation graphique d'une variable catégorielle sous forme de secteurs d'un disque, chaque secteur ayant un angle proportionnel à la fréquence de la catégorie qu'il représente.

# Interprétation
Alternative au [[Diagramme en barres]] pour des [[Types de données|données catégorielles]], plus adaptée pour visualiser des proportions d'un tout.

# Exemple
```chart
type: pie
labels: [Chimie, Physique, Info, Bio, Maths]
series:
  - title: Répartition
    data: [18, 25, 32, 14, 21]
```

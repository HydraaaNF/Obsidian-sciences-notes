# Définition
Représentation graphique d'une variable catégorielle : chaque catégorie est représentée par une barre dont la hauteur est proportionnelle à sa fréquence (ou son effectif).

# Interprétation
Adapté aux [[Types de données|données catégorielles]]. Permet une comparaison visuelle directe des fréquences entre catégories.

# Exemple
```chart
type: bar
labels: [Chimie, Physique, Info, Bio, Maths]
series:
  - title: Effectif
    data: [18, 25, 32, 14, 21]
```

#dmv-visualization

# Loi

La sensation perçue est une loi de puissance de l'intensité physique du stimulus :

$$S = I^N$$

avec $S$ la sensation perçue, $I$ l'intensité du stimulus et $N$ un exposant propre à la modalité sensorielle.

# Propriétés

Le comportement de la loi dépend de la valeur de l'exposant :

- $N > 1$ : la sensation croît plus vite que l'intensité, la modalité est expansive
- $N = 1$ : la sensation est proportionnelle à l'intensité, la modalité est linéaire
- $N < 1$ : la sensation croît plus lentement que l'intensité, la modalité est compressive

# Exemple

Exposants de quelques modalités, relevés sur la figure :

```chart
type: bar
labels: ["Choc électrique", "Saturation", "Longueur", "Aire", "Profondeur", "Luminosité"]
series:
  - title: Exposant N
    data: [3.5, 1.7, 1, 0.7, 0.67, 0.5]
```

Les courbes tracées pour ces modalités, de l'intensité physique portée en abscisse à la sensation perçue en ordonnée, s'ordonnent du plus convexe (le choc électrique) au plus concave (la luminosité), la longueur restant sur la diagonale.

# Interprétation

Pour l'encodage visuel, la loi dit qu'une même grandeur physique ne se lit pas de la même façon selon le canal qui la porte. Une longueur ($N = 1$) se lit proportionnellement à la valeur ; une aire ($N \approx 0{,}7$) sous-estime les grandes valeurs par rapport aux petites ; une luminance ($N \approx 0{,}5$) compresse fortement les écarts et rend les différences de teinte ou de clarté difficiles à ordonner. Ce constat fonde le classement des [[Canaux visuels et efficacité d'encodage|canaux visuels]] et éclaire les [[Erreurs de discrimination des encodages visuels|erreurs de discrimination]] mesurées sur les encodages élémentaires.

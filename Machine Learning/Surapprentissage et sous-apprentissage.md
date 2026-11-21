#ml-1

# Définition

Le **surapprentissage** (*overfitting*) est le défaut d'un modèle trop complexe, qui apprend trop près des données d'entraînement.

Le **sous-apprentissage** (*underfitting*) est le défaut d'un modèle trop simple, ou qui dispose de trop peu de données d'entraînement.

# Exemple

Sur un nuage de 40 points dont la tendance dessine un U, deux polynômes de degrés très différents ajustent le même nuage :

- **degré 1**, une droite : elle ignore la courbure et se trompe partout, c'est le sous-apprentissage ;
- **degré 18** : elle passe au plus près de chaque point et suit leur bruit, c'est le surapprentissage.

Un degré 2 ou 3 donne l'ajustement équilibré : il épouse la courbure sans suivre le bruit.

```chart
type: line
labels: ["0", "0.025", "0.05", "0.075", "0.1", "0.125", "0.15", "0.175", "0.2", "0.225", "0.25", "0.275", "0.3", "0.325", "0.35", "0.375", "0.4", "0.425", "0.45", "0.475", "0.5", "0.525", "0.55", "0.575", "0.6", "0.625", "0.65", "0.675", "0.7", "0.725", "0.75", "0.775", "0.8", "0.825", "0.85", "0.875", "0.9", "0.925", "0.95", "0.975"]
series:
  - title: "Points d'entraînement"
    data: [0.84, 0.72, 0.74, 0.73, 0.72, 0.58, 0.47, 0.40, 0.48, 0.51, 0.36, 0.20, 0.19, 0.37, 0.23, 0.06, 0.17, 0.07, 0.11, 0.11, 0.09, 0.20, 0.15, 0.12, 0.21, 0.26, 0.09, 0.22, 0.19, 0.29, 0.23, 0.38, 0.42, 0.44, 0.43, 0.54, 0.54, 0.58, 0.78, 0.74]
    showLine: false
    pointRadius: 4
    borderWidth: 0
  - title: "Degré 1 : sous-apprentissage"
    data: [0.44, 0.43, 0.43, 0.43, 0.42, 0.42, 0.42, 0.41, 0.41, 0.41, 0.40, 0.40, 0.40, 0.40, 0.39, 0.39, 0.39, 0.38, 0.38, 0.38, 0.37, 0.37, 0.37, 0.36, 0.36, 0.36, 0.35, 0.35, 0.35, 0.34, 0.34, 0.34, 0.33, 0.33, 0.33, 0.32, 0.32, 0.32, 0.31, 0.31]
    borderWidth: 2
    pointRadius: 0
```

```chart
type: line
labels: ["0", "0.025", "0.05", "0.075", "0.1", "0.125", "0.15", "0.175", "0.2", "0.225", "0.25", "0.275", "0.3", "0.325", "0.35", "0.375", "0.4", "0.425", "0.45", "0.475", "0.5", "0.525", "0.55", "0.575", "0.6", "0.625", "0.65", "0.675", "0.7", "0.725", "0.75", "0.775", "0.8", "0.825", "0.85", "0.875", "0.9", "0.925", "0.95", "0.975"]
series:
  - title: "Points d'entraînement"
    data: [0.84, 0.72, 0.74, 0.73, 0.72, 0.58, 0.47, 0.40, 0.48, 0.51, 0.36, 0.20, 0.19, 0.37, 0.23, 0.06, 0.17, 0.07, 0.11, 0.11, 0.09, 0.20, 0.15, 0.12, 0.21, 0.26, 0.09, 0.22, 0.19, 0.29, 0.23, 0.38, 0.42, 0.44, 0.43, 0.54, 0.54, 0.58, 0.78, 0.74]
    showLine: false
    pointRadius: 4
    borderWidth: 0
  - title: "Degré 18 : surapprentissage"
    data: [0.84, 0.73, 0.71, 0.79, 0.69, 0.55, 0.48, 0.47, 0.46, 0.42, 0.35, 0.29, 0.26, 0.23, 0.20, 0.17, 0.13, 0.10, 0.09, 0.10, 0.12, 0.15, 0.17, 0.18, 0.18, 0.18, 0.18, 0.19, 0.20, 0.24, 0.30, 0.36, 0.40, 0.43, 0.47, 0.51, 0.55, 0.58, 0.78, 0.74]
    borderWidth: 2
    pointRadius: 0
```

Abscisse : variable d'entrée ; ordonnée : variable à prédire. Mêmes 40 points, mêmes ajustements par moindres carrés : la droite passe à côté de la courbure, la courbe de degré 18 suit le bruit.

# Remarque

- Le surapprentissage se détecte en suivant l'erreur de validation : l'erreur d'entraînement diminue toujours et ne dit rien, tandis qu'une erreur de validation qui remonte signale le surapprentissage. Voir la partition des données en [[Jeux d'entraînement, de développement et de test|jeux d'entraînement, de développement et de test]].
- Un modèle trop complexe appartient à une famille riche en paramètres, dont le coût se lit dans l'[[Erreur d'approximation et erreur d'estimation|erreur d'estimation]] ; un modèle trop simple pèche au contraire par l'erreur d'approximation.
- Le modèle équilibré évite les deux excès à la fois : assez riche pour suivre la tendance réelle, assez contraint pour ne pas suivre le bruit. Ce compromis relève du principe de parcimonie du [[Rasoir d'Occam]].

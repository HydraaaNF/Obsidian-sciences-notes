#ml-1

# Modèle

Un jeu de données de classification binaire est un ensemble de points $(x_1, x_2, y)$ où :

- les $x_i$ sont des variables numériques ;
- $y$ est une variable **binaire**.

L'énoncé est le même que celui de la [[Régression linéaire]], mais $y$ vit désormais dans $\{0, 1\}$, et cela change tout.

# Exemple

Le même jeu de points, quatre dans chaque classe, ajusté par une droite et par une sigmoïde :

```chart
type: line
labels: ["-6", "-5.5", "-5", "-4.5", "-4", "-3.5", "-3", "-2.5", "-2", "-1.5", "-1", "-0.5", "0", "0.5", "1", "1.5", "2", "2.5", "3", "3.5", "4", "4.5", "5", "5.5", "6"]
yMin: -0.5
yMax: 1.5
xTitle: "x"
yTitle: "y"
series:
  - title: "Régression linéaire"
    data: [-0.282, -0.217, -0.152, -0.087, -0.022, 0.044, 0.109, 0.174, 0.239, 0.304, 0.37, 0.435, 0.5, 0.565, 0.63, 0.696, 0.761, 0.826, 0.891, 0.956, 1.022, 1.087, 1.152, 1.217, 1.282]
    pointRadius: 0
    borderWidth: 2
  - title: "Régression logistique"
    data: [0.0, 0.0, 0.0, 0.001, 0.002, 0.004, 0.008, 0.018, 0.039, 0.083, 0.168, 0.31, 0.5, 0.69, 0.832, 0.917, 0.961, 0.982, 0.992, 0.996, 0.998, 0.999, 1.0, 1.0, 1.0]
    pointRadius: 0
    borderWidth: 2
  - title: "Classe 0"
    data: [null, null, null, 0, 0, 0, 0, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null]
    showLine: false
    pointRadius: 5
    borderWidth: 0
  - title: "Classe 1"
    data: [null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, 1, 1, 1, 1, null, null, null]
    showLine: false
    pointRadius: 5
    borderWidth: 0
```

La droite sort de l'intervalle $[0, 1]$ aux deux extrémités, à $-0{,}28$ et $1{,}28$ : ces valeurs n'ont aucun sens comme probabilités. La sigmoïde, elle, reste dans $[0, 1]$ et sature de chaque côté.

# Remarque

Rien n'empêche d'ajuster $ax + b$ sur $y \in \{0, 1\}$, mais deux obstacles s'y opposent :

- la sortie est **non bornée** : $f(x) = 1.4$ ne signifie rien de précis, $f(x) = -0.3$ encore moins ;
- la [[Perte absolue et perte quadratique|perte quadratique]] continue de **pénaliser** des points déjà corrects : un point correct situé loin tire toute la droite à lui.

Il faut donc une sortie qui soit une **probabilité** ; c'est ce que construit la [[Régression logistique]].

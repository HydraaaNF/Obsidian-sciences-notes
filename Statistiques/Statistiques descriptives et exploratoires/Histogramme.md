# Définition
Pour des données continues, on regroupe les valeurs en classes (intervalles), et on représente chaque classe par un rectangle dont l'aire est proportionnelle à la fréquence $f_i$ de la classe.

# Interprétation
Permet de se faire une idée de la distribution sous-jacente et de repérer des comportements particuliers (valeurs aberrantes, nombre de modes).

# Remarque
Deux choix affectent fortement le rendu :
- le nombre de classes
- l'amplitude des classes (égale ou non, et si non, comment la choisir)

L'aire de chaque rectangle est proportionnelle à $f_i$ (pas nécessairement sa hauteur, si les classes n'ont pas la même amplitude).

# Exemple
```chart
type: bar
labels: ["[30,35[", "[35,40[", "[40,45[", "[45,50[", "[50,55[", "[55,60[", "[60,65[", "[65,70["]
series:
  - title: Effectif
    data: [8, 14, 29, 40, 52, 27, 26, 15]
```

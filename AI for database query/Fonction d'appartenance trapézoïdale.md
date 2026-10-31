# Définition
Une [[Fonction d'appartenance]] peut être définie par une **fonction trapézoïdale**, ce qui suffit à modéliser la plupart des concepts usuels. Il en existe trois types :
- **décroissante** : constante égale à $1$ jusqu'à un premier seuil, puis décroissance linéaire jusqu'à un second seuil, au-delà duquel elle vaut $0$ (ex. *young*) ;
- **croissante** : nulle jusqu'à un premier seuil, puis croissance linéaire jusqu'à un second seuil, au-delà duquel elle vaut $1$ (ex. *tall*) ;
- **croissante puis décroissante**, définie par **4 seuils** $a \le b \le c \le d$ (ex. *around 100*, centrée sur $100$).

# Propriétés
Pour le type à 4 seuils :
- croissance linéaire de $0$ à $1$ sur $[a, b]$ ;
- valeur constante $1$ sur $[b, c]$ : c'est le [[Noyau d'un ensemble flou]] ;
- décroissance linéaire de $1$ à $0$ sur $[c, d]$ ;
- valeur $0$ ailleurs : le [[Support d'un ensemble flou]] est $]a, d[$.

# Exemple
Illustration des trois types (seuils arbitraires) :

```chart
type: line
labels: ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "10", "11", "12"]
series:
  - title: Décroissante (4, 8)
    data: [1, 1, 1, 1, 1, 0.75, 0.5, 0.25, 0, 0, 0, 0, 0]
  - title: Croissante (4, 8)
    data: [0, 0, 0, 0, 0, 0.25, 0.5, 0.75, 1, 1, 1, 1, 1]
  - title: 4 seuils (a=2, b=4, c=8, d=11)
    data: [0, 0, 0, 0.5, 1, 1, 1, 1, 1, 0.67, 0.33, 0, 0]
beginAtZero: true
```

# Définition
Un [[Quantificateur flou]] est :
- **croissant** (*au moins 5*, *presque tous*, *la plupart*) ;
- **décroissant** (*au plus 5*, *une petite proportion*, …) ;
- **croissant-décroissant** (*environ 7*, *environ la moitié*).

# Exemple
- *Au moins 5* : croissant de $(3, 0)$ à $(5, 1)$, puis constant à partir de $5$.
- *Au plus 5* : constant égal à $1$ jusqu'à $5$, puis décroissant jusqu'à $0$ entre $5$ et $8$.
- *Environ 7* : triangle autour de $7$ (plus ou moins $2$).

```chart
type: line
labels: ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "10"]
series:
  - title: Au moins 5
    data: [0, 0, 0, 0, 0.5, 1, 1, 1, 1, 1, 1]
  - title: Au plus 5
    data: [1, 1, 1, 1, 1, 1, 0.67, 0.33, 0, 0, 0]
  - title: Environ 7
    data: [0, 0, 0, 0, 0, 0, 0.5, 1, 0.5, 0, 0]
beginAtZero: true
```

# Remarque
L'[[Interprétation de Yager par coupes de niveau α]] suppose un quantificateur **absolu croissant**.

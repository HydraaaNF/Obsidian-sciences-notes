#dmv-visualization

# Définition

L'erreur logarithmique d'un encodage visuel mesure la difficulté à discriminer deux valeurs portées par cet encodage : plus elle est élevée, moins la lecture est précise. Elle s'obtient expérimentalement, chaque valeur étant une estimation assortie d'un intervalle.

Neuf encodages élémentaires ont été évalués, notés T1 à T9, sur une échelle logarithmique allant de $1{,}0$ à $3{,}0$.

| Encodage | Erreur logarithmique |
| :--- | :--- |
| T1 | $\approx 1{,}3$ |
| T2 | $\approx 1{,}4$ |
| T3 | $\approx 1{,}55$ |
| T4 | $\approx 2{,}05$ |
| T5 | $\approx 2{,}3$ |
| T6 | $\approx 2{,}25$ |
| T7 | $\approx 2{,}65$ |
| T8 | $\approx 2{,}5$ |
| T9 | $\approx 2{,}6$ |

```chart
type: bar
labels: ["T1", "T2", "T3", "T4", "T5", "T6", "T7", "T8", "T9"]
series:
  - title: Erreur logarithmique
    data: [1.3, 1.4, 1.55, 2.05, 2.3, 2.25, 2.65, 2.5, 2.6]
```

# Interprétation

Les quatre erreurs les plus faibles sont celles des barres T1 à T4, de $1{,}3$ à $2{,}05$ ; viennent ensuite le camembert T6, à $2{,}25$, puis la barre T5, à $2{,}3$. Le bas du classement réunit donc les cinq barres et T6, entre $1{,}3$ et $2{,}3$. Les erreurs les plus fortes reviennent aux trois encodages fondés sur l'aire, T7, T8 et T9, de $2{,}5$ à $2{,}65$, dont la perception est moins précise.

L'écart entre T1 et T7 vaut environ un facteur deux sur l'erreur.

# Remarque

Les indices des encodages ne suivent pas strictement l'erreur croissante : T5, à $2{,}3$, dépasse T6, à $2{,}25$, et T9, à $2{,}6$, est inférieure à T7, à $2{,}65$. C'est le classement par valeur qui fait foi, pas l'ordre de numérotation.

Cette mesure expérimentale étaye le classement d'efficacité décrit dans les [[Canaux visuels et efficacité d'encodage]] et se rapproche, sans en découler, de la [[Loi de puissance de Stevens]] qui décrit l'intensité perçue ; l'[[Encodage par la couleur]] constitue un canal à part, dont la discrimination suit ses propres règles.

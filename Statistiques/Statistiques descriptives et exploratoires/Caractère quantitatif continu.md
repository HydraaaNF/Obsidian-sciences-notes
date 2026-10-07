# Définition

Pour un caractère quantitatif continu, par opposition à un [[Caractère quantitatif discret]], les observations sont regroupées en **classes** avant d'être représentées.

La distribution par classes s'établit en associant à chaque classe sa fréquence (le pourcentage du nombre total d'observations) et les fréquences cumulées.

La représentation graphique de cette distribution est l'**histogramme** : il est formé d'un rectangle par classe, et par construction, **l'aire de chaque rectangle est proportionnelle à la fréquence $f_i$** de la classe correspondante.

# Interprétation

L'histogramme sert à **représenter la distribution empirique** de la variable, afin de :

- se faire une idée de la distribution sous-jacente ;
- vérifier le comportement des données : valeurs aberrantes, nombre de modes, etc.

# Exemple

La distribution des revenus des contribuables, regroupés par tranches, associe à chaque classe la quantité $\ln(R - 2500)$, le pourcentage du nombre total de contribuables et les pourcentages cumulés :

| Tranche des revenus en francs | $\ln(R - 2500)$ | % du nombre total de contribuables | % cumulés |
|---|---|---|---|
| 2 500 | | 0,67 | |
| 5 000 | 3,39 | 30,18 | 0,67 |
| 10 000 | 3,87 | 27,50 | 30,85 |
| 15 000 | 4,10 | 17,09 | 58,35 |
| 20 000 | 4,24 | 14,45 | 75,44 |
| 30 000 | 4,44 | 7,01 | 89,90 |
| 50 000 | 4,68 | 1,66 | 96,90 |
| 70 000 | 4,83 | 0,81 | 98,56 |
| 100 000 | 4,99 | 0,51 | 99,37 |
| 200 000 | 5,30 | 0,10 | 99,88 |
| 400 000 | 5,60 | 0,02 | 99,98 |
| | | | 100 |

La dernière colonne donne les pourcentages cumulés, c'est-à-dire les fréquences cumulées de la distribution, à partir desquelles se construit la [[Fonction de répartition empirique]].

Histogramme des effectifs d'une variable continue, chaque barre correspond à une classe de largeur 0,5 :

```chart
type: bar
labels: ["0,5-1", "1-1,5", "1,5-2", "2-2,5", "2,5-3", "3-3,5", "3,5-4", "4-4,5", "4,5-5", "5-5,5", "5,5-6", "6-6,5", "6,5-7", "7-7,5", "7,5-8", "8-8,5", "8,5-9", "9-9,5", "9,5-10", "10-10,5", "10,5-11", "11-11,5"]
series:
  - title: Effectif
    data: [1, 2, 7, 8, 10, 10, 12, 12, 9, 6, 3, 6, 3, 2, 0, 2, 3, 1, 1, 1, 0, 1]
```

Valeurs relevées sur la figure, approximatives.

# Remarque

Le choix du découpage en classes reste ouvert : combien de classes ? des amplitudes égales ou non ? et si non, comment ? Le [[Lissage d'histogramme]] permet de s'affranchir de ces choix.

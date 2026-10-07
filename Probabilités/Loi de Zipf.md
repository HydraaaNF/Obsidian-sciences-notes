# Loi

La **loi de Zipf** est une distribution de probabilité qui reflète le fait que les **événements fréquents sont rares et les événements rares sont fréquents** : le produit du nombre d'occurrences (*count*) par le rang (*rank*), c'est-à-dire sa position dans le classement par fréquence décroissante, est approximativement constant :

$$\text{count} \times \text{rank} \simeq \text{cst}$$

# Exemple

Classement des équipes NBA par nombre de « likes » Facebook décroissant : le nombre de likes décroît très fortement avec le rang, suivant approximativement la loi de Zipf.

```chart
type: bar
labels: ["Lakers", "Bulls", "Heat", "Celtics", "Knicks", "Mavericks", "Thunder", "Magic", "Spurs", "Cavaliers", "Nuggets", "Suns", "Nets", "Rockets", "Clippers", "Pistons", "Trail Blazers", "Warriors", "Raptors", "Jazz", "76ers", "Hornets", "Hawks", "Timberwolves", "Bucks", "Kings", "Pacers", "Grizzlies", "Wizards", "Bobcats"]
series:
  - title: Likes Facebook (millions)
    data: [15.4, 7.5, 7.2, 6.8, 2.9, 2.4, 1.8, 1.7, 1.4, 0.9, 0.9, 0.7, 0.7, 0.6, 0.6, 0.5, 0.4, 0.4, 0.4, 0.4, 0.3, 0.3, 0.3, 0.3, 0.3, 0.3, 0.2, 0.2, 0.1, 0.1]
```

valeurs relevées sur la figure, approximatives.

# Remarque

L'[[Estimation par maximum de vraisemblance d'un modèle de Markov|estimation par maximum de vraisemblance]] des probabilités d'un [[Modèle de Markov pour les textes]] exige une **version lissée de l'estimateur** : voir le [[Lissage des probabilités|lissage des probabilités]].

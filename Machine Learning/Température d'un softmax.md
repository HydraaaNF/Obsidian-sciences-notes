#ml-1

# Définition

Soit $z \in \mathbb{R}^K$ un vecteur de $K$ scores et $T > 0$ une température. Tempérer la sortie de la [[Fonction softmax|fonction softmax]] consiste à diviser les scores par $T$ avant de les normaliser : on considère $\operatorname{softmax}(z/T)$.

# Interprétation

La température permet de relier le softmax au maximum des scores :

- $T \to 0$ : le plus grand score l'emporte seul, c'est un maximum dur (winner takes all).
- $T \to \infty$ : la distribution devient uniforme, chaque classe reçoit $1/K$.

Le softmax apparaît ainsi comme ce maximum, adouci (softened), et dérivable.

Après l'entraînement, $T$ est un vrai réglage : la génération de texte échantillonne dans $\operatorname{softmax}(z/T)$, ce qui correspond à la température des agents conversationnels, voir [[Génération d'une séquence]].

# Exemple

Sur trois classes (cat, dog, bird) de scores fixés, la probabilité attribuée à chaque classe évolue avec $T$ :

```chart
type: bar
labels: ["0.3", "1", "3"]
series:
  - title: cat
    data: [0.03, 0.24, 0.32]
  - title: dog
    data: [0.95, 0.67, 0.45]
  - title: bird
    data: [0, 0.09, 0.23]
```

À basse température la classe gagnante (dog) capte presque toute la masse, puis la distribution s'aplatit à mesure que $T$ augmente, et les trois classes finissent par se rapprocher de l'uniforme.

# Remarque

L'entraînement utilise $T = 1$, et cela ne fait rien perdre, pour deux raisons.

- La température se factorise dans les poids : $z/T = x(A/T)^\top + b/T$. Le réseau apprend donc sa propre température à travers ses poids, une redondance du même type que le choix $z_{\text{cat}} = 0$ dans la [[Fonction softmax|paramétrisation du softmax]].
- $T = 1$ garde les logits égaux aux log-odds : pour $K = 2$, le softmax redonne la sigmoïde de la [[Régression logistique]].

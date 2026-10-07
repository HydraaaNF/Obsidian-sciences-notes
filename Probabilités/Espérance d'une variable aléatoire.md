# Définition

L'**espérance** d'une [[Variable aléatoire]] $X$ est définie par :

- **cas discret** : si $X$ est une [[Variable aléatoire discrète|variable aléatoire discrète]],

$$\mathbb{E}[X] = \sum_{x \in X(\Omega)} x\,\mathbb{P}[X = x]$$

- **cas continu** : si $X$ est une [[Variable aléatoire continue|variable aléatoire continue]] de [[Probabilité à densité|densité]] $f$,

$$\mathbb{E}[X] = \int_{-\infty}^{\infty} x f(x)\,dx \qquad \text{(si l'intégrale converge)}$$

# Interprétation

L'espérance mesure le « centre de gravité » de la [[Loi d'une variable aléatoire|distribution]]. Elle est également appelée **moyenne** de $X$.

# Propriétés

L'espérance est linéaire :

- $\mathbb{E}[a] = a$ (l'espérance d'une variable aléatoire constante est égale à cette constante) ;
- $\mathbb{E}[X + a] = \mathbb{E}[X] + a$ ;
- $\mathbb{E}[aX] = a\,\mathbb{E}[X]$ ;
- $\mathbb{E}[X_1 + X_2] = \mathbb{E}[X_1] + \mathbb{E}[X_2]$.

Soit $X$ une variable aléatoire réelle discrète :

- l'espérance d'une variable aléatoire positive est positive ;
- si $X$ est positive et vérifie $\mathbb{E}(X) = 0$, alors $X$ est presque sûrement nulle ;
- si $X$ et $Y$ sont intégrables et [[Indépendance de variables aléatoires|indépendantes]], alors $XY$ est intégrable et $\mathbb{E}(XY) = \mathbb{E}(X)\mathbb{E}(Y)$.

# Remarque

- La [[Variance]] et les [[Moment d'ordre k|moments d'ordre k]] sont des quantités descriptives construites à partir de l'espérance.
- L'[[Espérance conditionnelle]] traite le cas où la valeur d'une autre variable aléatoire est connue.

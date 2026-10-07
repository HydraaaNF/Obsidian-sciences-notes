# Définition

Soit $(\Omega, \mathcal{F}, \mathbb{P})$ l'[[Espace probabilisé|espace probabilisé]] fondamental. On appelle [[Variable aléatoire|variable aléatoire]] à valeurs dans $\mathbb{R}^n$, ou **vecteur aléatoire de $\mathbb{R}^n$**, toute application mesurable $X$ de $\Omega$ dans $\mathbb{R}^n$.

Cela signifie que pour tout [[Tribu borélienne|borélien]] $B$ de $\mathbb{R}^n$, l'ensemble $X^{-1}(B)$, noté aussi $[X \in B]$, est un élément de la [[Tribu|tribu]] $\mathcal{F}$, c'est-à-dire un [[Évènement|évènement]].

## Cas continu

On dit qu'un vecteur aléatoire $X = (X_1, \dots, X_n)$ de $\mathbb{R}^n$ est **continu** s'il existe une fonction $f$ positive et intégrable sur $\mathbb{R}^n$ telle que, pour tout borélien $B$ de $\mathbb{R}^n$,

$$p_X(B) = \mathbb{P}(X \in B) = \int_B f(x) \mathop{}\!\mathrm{d}x.$$

Dans un tel cas, on note $f = f_X$ et on dit que $f_X$ est la **densité conjointe** des variables aléatoires réelles $X_1, \dots, X_n$.

# Propriétés

On admet le résultat suivant. Soit $X$ une application de $\Omega$ dans $\mathbb{R}^n$ et soit $X_1, \ldots, X_n$ ses composantes (ce sont donc des applications de $\Omega$ dans $\mathbb{R}$). Alors $X = (X_1, \ldots, X_n)$ est un vecteur aléatoire de $\mathbb{R}^n$ si et seulement si $X_1, \ldots, X_n$ sont des [[Variable aléatoire réelle|v.a.r.]].

# Exemple

1. On jette trois dés (supposés discernables, donc on peut les numéroter de 1 à 3) et on appelle $X_1, X_2, X_3$ les résultats respectifs des dés 1, 2 et 3. Alors $X = (X_1, X_2, X_3)$ est un vecteur aléatoire à valeurs dans $\mathbb{R}^3$. Plus précisément l'ensemble des valeurs prises par $X$ est le sous-ensemble suivant de $\mathbb{R}^3$ :

$$X(\Omega) = \{1, 2, 3, 4, 5, 6\} \times \{1, 2, 3, 4, 5, 6\} \times \{1, 2, 3, 4, 5, 6\} = \{1, 2, 3, 4, 5, 6\}^3$$

Un tel vecteur aléatoire est dit *discret* car ses composantes sont des [[Variable aléatoire discrète|v.a.r. discrètes]].

2. Une cible, constituée d'un disque de rayon $R$, est accrochée à un mur. Ce mur est un (morceau de) plan muni d'un repère orthonormé direct dont le centre est le centre de la cible. Le point d'impact $M(X, Y)$ de la fléchette dans ce repère est un vecteur aléatoire de $\mathbb{R}^2$.

A priori tout point de $\mathbb{R}^2$ est une valeur que peut prendre $(X, Y)$, de sorte que l'ensemble $M(\Omega)$ des valeurs prises par le couple $(X, Y)$ est $\mathbb{R}^2$ en entier. En effet, sauf mention du contraire, on n'a pas de raison de supposer que la fléchette arrive forcément dans la cible, ni même dans une région définie du plan (le mur, peut-être ?). Si par contre on admet que le lanceur atteint la cible à tous les coups, l'ensemble des valeurs prises par $(X, Y)$ devient le disque de centre $(0, 0)$ et de rayon $R$ :

$$M(\Omega) = \{(x, y) \in \mathbb{R}^2; x^2 + y^2 \leq R^2\}$$

Un tel vecteur aléatoire est dit *continu*.

3. On considère l'ensemble des adultes français de sexe masculin. L'expérience aléatoire consiste ici à choisir l'un de ces individus au hasard. Le couple constitué de la taille et du poids de cet individu constitue un vecteur aléatoire de $\mathbb{R}^2$, à coordonnées positives. Là aussi, il s'agit d'un vecteur aléatoire continu.

4. On considère deux ampoules au plafond d'une pièce. Le couple constitué des durées de vie $X$ et $Y$ de chaque lampe est un vecteur aléatoire continu de $\mathbb{R}^2$, tel que

$$(X, Y)(\Omega) = \mathbb{R}^+ \times \mathbb{R}^+$$

5. Un signal est filtré, émis, transmis sur une ligne, reçu et filtré. À chaque étape de ce processus se rajoute en pratique un *bruit* aléatoire. On peut par exemple être amené à considérer conjointement le couple de v.a.r. constitué du bruit d'émission et du bruit de transmission.

# Remarque

Pour la loi de probabilité d'un vecteur aléatoire, voir [[Loi d'un vecteur aléatoire]] ; pour l'étude des vecteurs aléatoires gaussiens, voir [[Vecteur gaussien]].

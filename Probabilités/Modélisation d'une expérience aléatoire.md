# Définition

Modéliser une expérience aléatoire, c'est déterminer l'ensemble, noté $\Omega$, des résultats possibles de l'expérience. C'est la première étape de la construction d'un [[Espace probabilisé]].

Le précepte de modélisation s'énonce ainsi :

> Commencer par définir mathématiquement l'ensemble $\Omega$ des résultats possibles de l'expérience aléatoire.

# Exemple

### L'erreur de D'Alembert : nécessité de la modélisation

On jette deux fois de suite une pièce bien équilibrée et on cherche la probabilité d'obtenir au moins une fois pile.

Il y a 4 possibilités, toutes équiprobables, qui sont $(p, p), (p, f), (f, p), (f, f)$, dont 3 réalisent l'[[Évènement|évènement]] étudié : la probabilité cherchée est donc $3/4$.

Un raisonnement erroné consiste à affirmer : « si c'est pile qui sort lors du premier jet, alors l'évènement est réalisé et il devient inutile de jeter une deuxième fois la pièce, de sorte qu'il n'y a en fait que 3 possibilités à considérer : $p, fp, ff$, dont deux réalisent l'évènement, donc la probabilité cherchée est en fait $2/3$ ».

L'erreur est de considérer ces 3 possibilités comme équiprobables, ce qui n'est pas le cas : l'éventualité $p$ correspond en fait à l'union des éventualités $pf$ et $pp$, dont la probabilité est de $2/4 = 1/2$ et non de $1/3$.

Modéliser l'expérience, c'est l'identifier à « jeter deux fois une pièce » : même si, en pratique, on ne jette pas la pièce une deuxième fois lorsqu'on a obtenu pile au premier jet, on peut imaginer qu'on la jette deux fois dans tous les cas de figure. L'ensemble des résultats possibles est alors

$$\Omega = \{(p, p), (p, f), (f, p), (f, f)\},$$

et en considérant que chaque éventualité est équiprobable, on obtient le résultat exact $3/4$.

### Le paradoxe de Bertrand

On considère un triangle équilatéral $ABC$ et son cercle circonscrit, et l'on choisit au hasard une corde de ce cercle. Quelle est la probabilité que la longueur de la corde choisie dépasse celle du côté du triangle ?

Selon la façon de préciser ce choix « au hasard », on obtient des résultats numériques différents. Deux solutions :

1. Par raison de symétrie, on peut considérer que l'une des extrémités de la corde est fixée sur le cercle, en $A$ pour fixer les idées, et qu'on choisit au hasard l'autre extrémité, notée $M$. Alors $AM \geq AB$ si et seulement si $M$ est choisie entre $B$ et $C$ à l'opposé de $A$. La probabilité que cela arrive est $1/3$.

2. À un point $I$ à l'intérieur du cercle, distinct de $O$, correspond une seule corde dont il est le milieu. En effet, soit $I$ un tel point et soit $[MN]$ une corde dont $I$ est le milieu : comme $M$ et $N$ sont sur le cercle, ils sont équidistants de $O$, donc la droite $(OI)$ est la médiatrice du segment $[MN]$ ; la corde dont $I$ est le milieu s'obtient en construisant la perpendiculaire à $(OI)$ passant par $I$. Choisir une corde au hasard est donc équivalent à choisir un point $I$ au hasard à l'intérieur du cercle. La corde $[MN]$ est plus longue que le côté du triangle $ABC$ si le point $I$ a été choisi à l'intérieur du cercle inscrit au triangle. Or, puisque le triangle est équilatéral, ce cercle inscrit a un rayon moitié du cercle circonscrit ; le point $I$ étant choisi de façon [[Loi uniforme sur un domaine|uniforme]] dans le disque, la probabilité cherchée est le rapport des aires des deux disques :

$$\frac{\pi(r/2)^2}{\pi r^2} = 1/4.$$

Les deux solutions paraissent justes : c'est le paradoxe. En réalité, l'expérience aléatoire proposée (« choisir une corde ») est mal définie ; il conviendrait d'expliquer ce que l'on entend par « choisir une corde » (par exemple : fixer une extrémité et choisir l'autre, ou bien : choisir le milieu de la corde). Si l'on cherche à écrire l'ensemble $\Omega$ des résultats possibles de l'expérience aléatoire, on se rend vite compte que c'est impossible sans préciser la façon de choisir la corde : c'est encore un défaut de modélisation.

# Remarque

La nécessité de la modélisation apparaît dans les deux exemples : une expérience « au hasard » doit être précisée avant tout calcul, sans quoi la même question peut recevoir plusieurs réponses, et une éventualité ne peut être déclarée équiprobable que si la modélisation le justifie. Définir l'ensemble $\Omega$ des résultats possibles est donc la première étape de tout calcul de probabilité.

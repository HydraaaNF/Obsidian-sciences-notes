# Définition

Une **variable aléatoire** $X$ sur un [[Espace probabilisé|espace des possibles]] $\Omega$ est une fonction $X : \Omega \to \mathbb{R}$, encore appelée [[Variable aléatoire réelle|variable aléatoire réelle]], qui associe un nombre réel $X(\omega)$ à chaque issue $\omega \in \Omega$.

Autrement dit, une variable aléatoire est une fonction qui envoie l'espace des possibles vers des valeurs, qui peuvent être [[Variable aléatoire discrète|discrètes]] ou [[Variable aléatoire continue|continues]].

Dans le cas discret, $X$ prend ses valeurs dans un ensemble $E$ fini ou dénombrable : toute application $X : \Omega \to E$ vérifiant $X^{-1}(\{k\}) \in \mathcal{F}$ pour tout $k \in E$ est une variable aléatoire discrète ; l'ensemble $X(\Omega) \subset E$ est son **espace des états**.

# Propriétés

L'**image réciproque** d'une variable aléatoire $X$ est définie par

$$A_x = \{\omega \in \Omega \text{ tel que } X(\omega) = x\}$$

avec les propriétés suivantes :

- $A_x \cap A_y = \emptyset$ si $x \neq y$ ;
- $\bigcup_{x \in \mathbb{R}} A_x = \Omega$.

Les événements $A_x$ forment ainsi une partition de l'espace des possibles : chaque issue appartient à un et un seul d'entre eux.

# Interprétation

Il est souvent plus commode de travailler dans l'espace d'événements défini par la collection des événements $A_x$ lorsque l'intérêt porte uniquement sur la valeur expérimentale de la variable aléatoire $X$. Dans le cas d'une [[Variable aléatoire discrète|variable aléatoire discrète]], ces événements suffisent à décrire sa [[Loi d'une variable aléatoire|loi]].

# Exemple

On choisit au hasard entre 0 et 1, trois fois de suite, et on observe le nombre de 1 obtenus : $X(\omega)$ est le nombre de 1 de l'issue $\omega$.

| $\omega \in \Omega$  | 111   | 110   | 101   | 100   | 011   | 010   | 001   | 000   |
| -------------------- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| $\mathbb{P}(\omega)$ | 0.125 | 0.125 | 0.125 | 0.125 | 0.125 | 0.125 | 0.125 | 0.125 |
| $X(\omega)$          | 3     | 2     | 2     | 1     | 2     | 1     | 1     | 0     |

Les images réciproques des valeurs prises par $X$ sont

$$A_0 = \{(0, 0, 0)\}$$

$$A_1 = \{(1, 0, 0), (0, 1, 0), (0, 0, 1)\}$$

$$A_2 = \{(1, 1, 0), (1, 0, 1), (0, 1, 1)\}$$

$$A_3 = \{(1, 1, 1)\}$$

ce qui réduit l'espace des possibles de dimension 8 à un espace d'événements de dimension 4. Avec $n$ essais, $2^n$ points de l'espace des possibles se réduisent ainsi à $n + 1$ événements.

La durée de vie d'un composant est une autre variable aléatoire : l'espace des possibles correspondant est difficile à imaginer.

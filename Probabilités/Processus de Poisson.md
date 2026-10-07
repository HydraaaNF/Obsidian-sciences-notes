# Définition

Dans les applications courantes, le processus $(A(t))_{t \geq 0}$ peut être modélisé par un **processus de Poisson** : il s'agit d'un [[Processus de comptage|processus de comptage]] vérifiant des propriétés qui s'avèrent raisonnables dans des contextes variés.

Soit $\lambda > 0$. Le processus de comptage $(A(t))_{t \geq 0}$ est un processus de Poisson de taux $\lambda$ si :

1. pour $0 < t_1 < \dots < t_n$, les [[Variable aléatoire|variables aléatoires]] $A(t_1), A(t_2) - A(t_1), \dots, A(t_n) - A(t_{n-1})$ sont [[Indépendance de variables aléatoires|indépendantes]] ;
2. pour $0 < s < t$, la loi de la variable aléatoire $A(t) - A(s)$ ne dépend que de $t - s$ ;
3. pour $t$ au voisinage de $0$, on a

- $\mathbb{P}(A(t) = 0 \mid A(0) = 0) = 1 - \lambda t + o(t)$ ;
- $\mathbb{P}(A(t) = 1 \mid A(0) = 0) = \lambda t + o(t)$.

# Interprétation

- Le point 1 exprime qu'un processus de Poisson est **à accroissements indépendants**.
- Le point 2 exprime qu'un processus de Poisson est **à accroissements stationnaires**.
- Le point 3 exprime que pendant un **petit** intervalle de temps de durée $t$, la probabilité d'une arrivée est **approximativement proportionnelle** à $t$ (le taux $\lambda$ représentant le coefficient de proportionnalité).

Un tel processus est en général utilisé pour compter les occurrences d'un évènement pendant l'intervalle de temps $]0, t]$ lorsque ces trois propriétés semblent raisonnables dans le contexte étudié (par exemple : arrivée d'un client à un serveur, arrivée de tâches à un calculateur, arrivée d'un véhicule à un péage d'autoroute, accident, accouchement...). Il est donc particulièrement intéressant dans le contexte des [[File d'attente|files d'attente]] pour représenter le processus des arrivées. Il ne faudrait pourtant pas croire que c'est un modèle universel : voir la remarque ci-dessous.

# Propriétés

On admet la conséquence suivante de la définition : pour des instants $t_0 < \dots < t_n < t_{n+1}$ et des entiers $i_0, \dots, i_n, i_{n+1}$,

$$\mathbb{P}(A(t_{n+1}) = i_{n+1} \mid A(t_0) = i_0, \dots, A(t_n) = i_n) = \mathbb{P}(A(t_{n+1}) = i_{n+1} \mid A(t_n) = i_n)$$

L'égalité ci-dessus exprime que $(A(t))_{t \geq 0}$ vérifie la **propriété de Markov à temps continu** : un processus de Poisson est donc une [[Chaîne de Markov à temps continu|chaîne de Markov à temps continu]]. On a également

$$\mathbb{P}(A(t_{n+1}) = i_{n+1} \mid A(t_n) = i_n) = \mathbb{P}(A(t_{n+1} - t_n) = i_{n+1} \mid A(0) = i_n)$$

ce qui exprime que cette chaîne de Markov est **homogène** (dans le temps).

Ainsi, si à l'instant $s$ on a constaté $i$ arrivées, la probabilité de constater $j - i$ arrivées supplémentaires pendant un intervalle de temps de durée $t$ ne dépend pas de $s$, mais seulement de $t$ ; elle ne dépend pas non plus de la trajectoire passée du processus. En particulier, la probabilité de constater une arrivée supplémentaire pendant $t$ petit à partir d'un instant $s$ quelconque est

$$\mathbb{P}(A(s+t) = i+1 \mid A(s) = i) = \lambda t + o(t) \sim_{t \rightarrow 0} \lambda t$$

# Exemple

Vu comme [[Chaîne de Markov à temps continu|chaîne de Markov à temps continu]], un processus de Poisson de taux $\lambda$ admet pour taux de transition instantanés $a_{i,i+1} = \lambda$ pour tout $i$, et $a_{i,j} = 0$ pour $|j-i| \geq 2$.

# Remarque

Il résulte immédiatement du troisième point de la définition que, pour $t$ au voisinage de $0$,

$$\forall k \geq 2 \quad \mathbb{P}(A(t) = k \mid A(0) = 0) = o(t)$$

Pendant un petit intervalle de temps, il est donc **rare** d'observer deux arrivées. En pratique, cela interdit de modéliser le processus des arrivées par un processus de Poisson lorsque plusieurs clients peuvent arriver « en même temps ». Dans un tel cas (modélisation du trafic Internet par exemple), il existe des généralisations du processus de Poisson, dites **processus de Poisson composés**, qui permettent d'essayer de rendre compte de ces situations difficiles.

Le nom du processus provient de la loi suivie par $A(t)$ : voir [[Loi du processus de Poisson]] et [[Loi de Poisson]].

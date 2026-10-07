# Définition

Le [[Processus d'arrivée et de service|processus des arrivées]] $(A(t))_{t \geq 0}$ d'un [[File d'attente|système d'attente]] est un **processus de comptage**, c'est-à-dire un processus stochastique à temps continu, à valeurs dans $\mathbb{N}$ et croissant avec $t$ ; $A(t)$ désigne le nombre d'arrivées de clients dans l'intervalle de temps $]0, t]$.

On note $T_n$ l'instant de la $n$-ième arrivée ($n \in \mathbb{N}^*$) et $X_n$ le temps séparant la $n$-ième arrivée de la $(n+1)$-ième :

$$X_0 = T_1$$

$$X_n = T_{n+1} - T_n \quad (n \geq 1)$$

On a donc

$$T_n = \sum_{i=0}^{n-1} X_i$$

# Théorème

Soit $(A(t))_{t \geq 0}$ un processus de comptage. Avec les notations ci-dessus, on a les égalités suivantes entre [[Évènement|évènements]] :

$$\forall n \in \mathbb{N}, \quad [A(t) \leq n] = [T_{n+1} > t]$$

$$\forall n \in \mathbb{N}^*, \quad [A(t) \geq n] = [T_n \leq t]$$

# Propriétés

**Corollaire.** Soit $(A(t))_{t \geq 0}$ un processus de comptage. Pour tout $n \in \mathbb{N}^*$, on a :

$$[A(t) = n] = [T_n \leq t] \cap [T_{n+1} > t]$$

$$\mathbb{P}(A(t) = n) = \mathbb{P}(T_n \leq t) - \mathbb{P}(T_{n+1} \leq t)$$

# Interprétation

- La relation $[A(t) \leq n] = [T_{n+1} > t]$ signifie qu'il y a au plus $n$ arrivées sur $]0, t]$ si et seulement si la $(n+1)$-ième arrivée n'a pas encore eu lieu à l'instant $t$.
- La relation $[A(t) \geq n] = [T_n \leq t]$ signifie qu'il y a au moins $n$ arrivées sur $]0, t]$ si et seulement si la $n$-ième arrivée a eu lieu au plus tard à l'instant $t$.

# Remarque

Le [[Processus de Poisson]] est le principal modèle de processus de comptage ; ses [[Temps d'inter-arrivée d'un processus de Poisson|temps d'inter-arrivée]] $X_n$ sont indépendants et identiquement distribués de loi exponentielle.

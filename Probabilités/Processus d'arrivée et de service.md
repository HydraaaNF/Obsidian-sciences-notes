# Modèle

On considère l'[[Espace probabilisé|espace probabilisé]] fondamental $(\Omega, \mathcal{F}, \mathbb{P})$. Pour chaque instant $t \geq 0$, on s'intéresse au nombre $N(t)$ de clients présents dans la [[File d'attente|file]] à l'instant $t$. C'est une [[Variable aléatoire discrète|v.a. discrète]] (à valeurs dans $\mathbb{N}$). On dit que la famille de v.a. $(N(t))_{t \in \mathbb{R}^+}$, indexée par l'intervalle $\mathbb{R}^+$, est un **processus stochastique à temps continu**. Au besoin, on note $N(t, \omega)$ la valeur de la v.a. $N(t)$ en $\omega \in \Omega$.

On appelle $A(t)$ le nombre d'arrivées de clients dans l'intervalle de temps $]0, t]$, avec le plus souvent la convention $A(0) = 0$. Le processus stochastique $(A(t))_{t \geq 0}$ est un [[Processus de comptage|processus de comptage]], c'est-à-dire un processus stochastique à temps continu à valeurs dans $\mathbb{N}$ et croissant avec $t$.

On note $T_n$ la date d'arrivée du $n$-ième client ($n \in \mathbb{N}^*$), de sorte que la durée entre l'arrivée du $n$-ième client et l'arrivée du $(n+1)$-ième client ($n = 1, 2, \dots$) est la v.a. $X_n = T_{n+1} - T_n$. Les v.a. $X_0 = T_1, X_1 = T_2 - T_1, \dots, X_n = T_{n+1} - T_n, \dots$ sont [[Variable aléatoire continue|continues]] et à valeurs dans $[0, +\infty[$. On suppose que ces v.a. (qui sont les **temps d'inter-arrivées**) sont i.i.d.

On note $S_n$ la durée du service du $n$-ième client ($n = 1, 2, \dots$). Les v.a. $S_n$ sont continues et à valeurs dans $[0, +\infty[$. On suppose qu'elles sont i.i.d. et qu'elles sont indépendantes des temps d'inter-arrivées.

# Remarque

La loi des $X_n = T_{n+1} - T_n$ et celle des $S_n$ sont les critères essentiels dans l'étude des [[File d'attente|files d'attente]]. Dans le cas où les temps d'inter-arrivées suivent une loi exponentielle (sans mémoire), le processus d'arrivée $(A(t))_{t \geq 0}$ est un [[Processus de Poisson]].

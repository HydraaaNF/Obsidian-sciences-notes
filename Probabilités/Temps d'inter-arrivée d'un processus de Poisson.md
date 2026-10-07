# Théorème

On note $(X_n)_{n \in \mathbb{N}}$ la suite des [[Variable aléatoire|variables aléatoires]] représentant les durées entre deux arrivées successives d'un [[Processus de comptage|processus de comptage]] :

$$X_0 = T_1$$

$$X_n = T_{n+1} - T_n \quad (n \geq 1)$$

où $T_n$ désigne l'instant de la $n$-ième arrivée.

**Processus de Poisson et temps d'inter-arrivées.** Un processus de comptage $(A(t))_{t \geq 0}$ est un [[Processus de Poisson|processus de Poisson]] de taux $\lambda$ si et seulement si les variables aléatoires $X_n$ sont [[Indépendance de variables aléatoires|indépendantes]] et identiquement distribuées (i.i.d.) de loi commune $\mathcal{E}(\lambda)$, la [[Loi exponentielle|loi exponentielle]] de paramètre $\lambda$.

### Démonstration

On ne démontre pas ce théorème ; on vérifie que si $(A(t))_{t \geq 0}$ est un processus de Poisson de taux $\lambda$, alors $X_0 \sim \mathcal{E}(\lambda)$ sous l'hypothèse $A(0) = 0$.

Pour cela, on calcule la [[Fonction de répartition|fonction de répartition]] de $X_0$. Puisque $X_0$ est continue et à valeurs positives, $F_{X_0}(t) = 0$ pour $t \leq 0$. Pour $t > 0$, on a, en vertu de l'égalité $[A(t) \geq 1] = [T_1 \leq t]$ :

$$\begin{aligned} F_{X_0}(t) &= \mathbb{P}(X_0 \leq t) \\ &= \mathbb{P}(T_1 \leq t) \\ &= \mathbb{P}(A(t) \geq 1) \\ &= 1 - \mathbb{P}(A(t) = 0) \\ &= 1 - e^{-\lambda t} \end{aligned}$$

car sous l'hypothèse $A(0) = 0$, la variable aléatoire $A(t)$ suit la [[Loi du processus de Poisson|loi de Poisson]] de paramètre $\lambda t$. On reconnaît bien la fonction de répartition de la loi exponentielle de paramètre $\lambda$.

On pourrait ensuite prouver que, toujours sous l'hypothèse $A(0) = 0$ :

$$\begin{aligned} \mathbb{P}(X_0 > t, X_1 > s) &= \mathbb{P}(T_1 > t, T_2 - T_1 > s) \\ &= e^{-\lambda t} e^{-\lambda s} \end{aligned}$$

ce qui prouverait que $X_1$ est elle aussi distribuée suivant la loi $\mathcal{E}(\lambda)$ et est indépendante de $X_0$. Il resterait à généraliser ce calcul en déterminant la [[Loi d'un vecteur aléatoire|loi conjointe]] de $(X_0, X_1, \dots, X_n)$. Cela prouverait un des deux sens de l'équivalence donnée dans le théorème, mais il faudrait encore prouver la réciproque.

# Interprétation

La condition nécessaire et suffisante donnée dans ce théorème peut être choisie comme **définition** du processus de Poisson. Dans l'étude des [[File d'attente|files d'attente]] markoviennes, c'est ce point de vue qui est adopté.

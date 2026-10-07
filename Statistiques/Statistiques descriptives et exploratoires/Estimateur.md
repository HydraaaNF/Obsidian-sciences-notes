# Définition

La théorie de l'échantillonnage se propose d'étudier les propriétés du $n$-uplet $(X_1, \dots, X_n)$ et des caractéristiques le résumant à partir de la loi mère supposée, ainsi que ce qui se passe lorsque la taille de l'échantillon est élevée.

Soit $\theta$ un paramètre de la loi mère, $\theta$ inconnu. Par exemple, $\theta$ peut représenter l'[[Espérance d'une variable aléatoire|espérance]] $\mathbb{E}[X]$, la [[Variance|variance]] $\mathbb{V}(X)$, la [[Moyenne, médiane et mode|médiane]] de $X$, le [[Moment d'ordre k|moment d'ordre 3]] de la loi mère, etc. On veut estimer $\theta$ à partir de l'[[Échantillon et échantillonnage|échantillon]]. On introduit pour cela la notion d'estimateur.

Un **estimateur** de $\theta$ est une [[Variable aléatoire|variable aléatoire]] $T$ qui est fonction (mesurable) du $n$-uplet $(X_1, \dots, X_n)$ à valeurs dans un domaine acceptable pour $\theta$ :

$$T = f(X_1, \dots, X_n).$$

L'**estimation** de $\theta$ à partir des observations $(x_1, \dots, x_n)$ est donnée par la réalisation

$$\begin{aligned} T(\omega) &= f(X_1(\omega), \dots, X_n(\omega)) \\ &= f(x_1, \dots, x_n). \end{aligned}$$

# Interprétation

Un estimateur $T$ est une variable aléatoire qui correspond à une méthode générale (« une stratégie ») pour estimer un paramètre $\theta$ : on le note donc avec une lettre majuscule. Une estimation, ou valeur estimée, de $\theta$ correspond à une réalisation de $T$ : cette valeur (généralement numérique) est associée à une série d'observations $(x_1, \dots, x_n)$. On la note $T(\omega)$, ou à l'aide d'une lettre minuscule.

# Remarque

Par définition, un estimateur dépend de la taille de l'échantillon $(X_1, \dots, X_n)$. Afin d'alléger les expressions, on ne rappelle pas toujours cette dépendance dans la notation de l'estimateur : on écrit $T$ de préférence à $T_n$. On utilise la notation $T_n$ lorsque l'on veut souligner cette dépendance.

Un estimateur s'étudie à travers ses propriétés : sa [[Estimateur convergent|convergence]], son [[Biais d'un estimateur|biais]] et son [[Erreur quadratique moyenne|erreur quadratique moyenne]].

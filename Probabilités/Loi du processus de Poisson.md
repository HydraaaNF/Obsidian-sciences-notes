# Théorème

**Loi de $A(t)$.** Soit $(A(t))_{t \geq 0}$ un [[Processus de Poisson|processus de Poisson]] de taux $\lambda$. Alors la variable aléatoire $A(t)$ est distribuée, sous l'hypothèse $A(0) = 0$, suivant la [[Loi de Poisson|loi de Poisson]] de paramètre $\lambda t$ :

$$\forall n \in \mathbb{N} \quad \mathbb{P}(A(t) = n \mid A(0) = 0) = e^{-\lambda t} \frac{(\lambda t)^n}{n!}$$

# Propriétés

**Corollaire.** Sous les mêmes hypothèses, pour tous $s$ et $t$ réels positifs,

$$\forall j \geq i \geq 0 \quad \mathbb{P}(A(s+t) = j \mid A(s) = i) = e^{-\lambda t} \frac{(\lambda t)^{j-i}}{(j-i)!}$$

# Interprétation

Ce résultat justifie le nom du processus : sous l'hypothèse $A(0) = 0$, le nombre d'arrivées comptabilisées sur un intervalle de durée $t$ suit une loi de Poisson de paramètre $\lambda t$. Le corollaire étend l'énoncé au nombre d'arrivées supplémentaires au cours d'un intervalle de durée $t$, conditionnellement au nombre $i$ d'arrivées déjà comptabilisées à l'instant $s$ : cette loi ne dépend ni de $s$, ni du nombre $i$ d'arrivées, mais seulement de la durée $t$ et de l'écart $j - i$.

# Remarque

Le processus peut aussi être décrit par la suite de ses [[Temps d'inter-arrivée d'un processus de Poisson|temps d'inter-arrivée]], c'est-à-dire des durées entre deux arrivées successives.

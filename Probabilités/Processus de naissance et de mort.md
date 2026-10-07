# Définition

Un cas particulièrement fréquent est celui où les transitions instantanées se font entre états « voisins » : cela arrive lorsqu'il est très improbable de constater deux arrivées (ou plus) en même temps, ou deux départs (correspondant à des fins de service) en même temps.

La [[Chaîne de Markov à temps continu|CMTC]] $(N_t)_{t \geq 0}$ d'espace des états $E \subset \mathbb{N}$ est un **processus de naissance et de mort** (PNM) si pour tout $(i, j) \in E^2$ avec $j \neq i$, l'on a :

$$j \notin \{i-1, i+1\} \implies a_{i,j} = 0$$

On note alors pour $i \in E$ :

$$\forall i \geq 0 \qquad \lambda(i) = a_{i,i+1}$$

$$\forall i \geq 1 \qquad \mu(i) = a_{i,i-1}$$

Autrement dit, pour un PNM les seules transitions observées pendant un petit intervalle de temps ont lieu entre états « voisins ».

Une transition vers $i + 1$ est interprétée comme une *naissance* et on note $\lambda(i)$ le taux de transition correspondant. De même, une transition vers $i - 1$ est interprétée comme une *mort*, le taux de transition correspondant étant $\mu(i)$.

# Interprétation

- Le vocabulaire de naissance et de mort provient de la modélisation de l'effectif d'une population fluctuant au gré des naissances et des morts (naturelles ou non), dans des études d'interaction proies-prédateurs notamment ; ces modèles servent aussi à l'étude théorique de la performance des réseaux (téléphonie, téléinformatique).
- L'objectif principal de l'étude est de déterminer la distribution limite $\pi$ si elle existe : $\pi_j$ représente la probabilité de trouver $j$ clients dans le système à un instant quelconque du régime stationnaire, s'il y en a un (voir [[Système ergodique]]).

# Propriétés

## Équations de balance

Pour qu'un « équilibre » s'établisse, il est nécessaire que le « flux entrant » soit égal au « flux sortant » en régime stationnaire (sinon un tel régime n'existerait pas). Cette idée empirique peut être justifiée rigoureusement. Ici, cela donne :

$$\pi_0 \lambda(0) = \pi_1 \mu(1)$$

et pour $j \geq 1$ :

$$\pi_{j-1} \lambda(j-1) + \pi_{j+1} \mu(j+1) = \pi_j \lambda(j) + \pi_j \mu(j)$$

Si pour $j \geq 0$ on pose $\alpha_j = \lambda(j)\pi_j - \mu(j+1)\pi_{j+1}$, on voit qu'on obtient $\alpha_{j-1} = \alpha_j$ pour $j \geq 1$, avec $\alpha_0 = 0$, donc tous les $\alpha_j$ sont nuls, d'où, en supposant que les $\mu(k)$ sont tous non nuls :

$$\forall j \geq 1 \quad \pi_j = \frac{\lambda(j-1)}{\mu(j)} \pi_{j-1}$$

## Cas $E = \mathbb{N}$

$E = \mathbb{N}$ lorsque la [[File d'attente|file]] a une capacité illimitée et que le nombre potentiel de clients est infini ($K_5 = K_6 = \infty$ dans la [[Nomenclature de Kendall|nomenclature de Kendall]]). On en déduit :

$$\forall j \geq 1 \quad \pi_j = \pi_0 \prod_{k=1}^j \frac{\lambda(k-1)}{\mu(k)}$$

Pour calculer $\pi_0$, on utilise la condition de normalisation $\sum_{j \in E} \pi_j = 1$ :

$$\pi_0 \left( 1 + \sum_{j=1}^{+\infty} \prod_{k=1}^j \frac{\lambda(k-1)}{\mu(k)} \right) = 1$$

si **la série** qui intervient dans cette formule **converge**. Ceci fournit la condition d'existence de la distribution stationnaire. Sous cette condition, on obtient :

$$\pi_0 = \left( 1 + \sum_{j=1}^{+\infty} \prod_{k=1}^j \frac{\lambda(k-1)}{\mu(k)} \right)^{-1}$$

## Cas $E = \{0, 1, \dots, s\}$

Si $\#E = s + 1$ est fini (cas d'un nombre fini de places dans la zone d'attente, ou cas d'un nombre fini de clients potentiels), le raisonnement est analogue, mais la « dernière » équation est différente des autres :

$$\lambda(s-1)\pi_{s-1} - \mu(s)\pi_s = 0$$

On trouve une formule analogue à celle du cas $E = \mathbb{N}$. Comme on tombe sur une somme finie et non sur une série, il n'y a pas ici de critère d'existence de la solution.

# Remarque

Les files markoviennes [[File M-M-1|M/M/1]], [[File M-M-infini|M/M/∞]] et [[File M-M-n-K|M/M/n/K]] sont des cas particuliers de processus de naissance et de mort.

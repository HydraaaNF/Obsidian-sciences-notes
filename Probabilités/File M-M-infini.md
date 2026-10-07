# Définition

La **file $M/M/\infty$** est un [[File d'attente|système d'attente]] comportant une infinité de serveurs montés en parallèle, de capacité infinie (voir la [[Nomenclature de Kendall]] pour cette notation). Dans ce modèle, il n'y a aucune attente.

On s'intéresse au processus $(N(t))_{t \geq 0}$ qui compte le nombre de clients dans le système à l'instant $t$. Le processus des arrivées $(A(t))_{t \geq 0}$ est un [[Processus de Poisson]] de taux $\lambda > 0$, et à chaque serveur correspond une [[Processus d'arrivée et de service|durée de service]] exponentielle de paramètre $\mu > 0$. Si $S_i$ est le temps de service du $i$-ème client, les v.a. $S_i$ sont supposées indépendantes (de loi $\mathcal{E}(\mu)$), et sont également indépendantes des [[Temps d'inter-arrivée d'un processus de Poisson|temps d'inter-arrivées]].

Grâce à la propriété d'absence de mémoire de la [[Loi exponentielle|loi exponentielle]], $(N(t))_{t \geq 0}$ est une [[Chaîne de Markov à temps continu|CMTCH]]. On montre en fait que c'est un [[Processus de naissance et de mort|PNM]].

# Interprétation

La file $M/M/\infty$ est utilisée en pratique comme approximation de la file $M/M/n$ ou de la [[File M-M-n-K|M/M/n/K]] lorsque le nombre $n$ de serveurs est assez grand pour servir immédiatement tout nouveau client. En effet, les valeurs numériques exactes des paramètres intéressants pour ces deux files sont pénibles à calculer si $n$ est grand ; la file $M/M/\infty$ est un modèle permettant d'avoir une bonne idée a priori de la valeur de ces paramètres, avant éventuellement une étude plus fine.

# Propriétés

## Taux de transition

Déterminons les taux de transition ; le calcul le plus difficile est celui de $a_{k,k-1}$. Pour $k \geq 1$ :

$$\begin{aligned} p_{k,k-1}(\delta t) &= \mathbb{P}(N(t + \delta t) = k - 1 \mid N(t) = k) \\ &= \mathbb{P}(A(\delta t) = 0) \binom{k}{1} \mathbb{P}(S \leq \delta t) \mathbb{P}(S > \delta t)^{k-1} + o(\delta t) \\ &= k e^{-\lambda \delta t} (1 - e^{-\mu \delta t}) e^{-(k-1)\mu \delta t} + o(\delta t) \\ &= k \mu \delta t + o(\delta t) \end{aligned}$$

De même on trouve immédiatement

$$\begin{aligned}\forall k &\geq 0 \quad p_{k,k+1}(\delta t) = \lambda \delta t + o(\delta t) \\ p_{0,0}(\delta t) &= 1 - \lambda \delta t + o(\delta t) \\ \forall k &\geq 1 \quad p_{k,k}(\delta t) = 1 - (\lambda + k\mu)\delta t + o(\delta t)\end{aligned}$$

Ces quatre relations montrent que $(N(t))_{t \geq 0}$ est un [[Processus de naissance et de mort|PNM]] dont les taux de transition sont

- $\forall k \in \mathbb{N} \quad \lambda(k) = \lambda$ ;
- $\forall k \geq 1 \quad \mu(k) = k \mu$.

## Régime stationnaire

La distribution limite d'un [[Processus de naissance et de mort|PNM]] donne, pour $j \geq 1$ :

$$\begin{aligned} \pi_j &= \pi_0 \prod_{k=1}^j \frac{\lambda}{k\mu} \\ &= \pi_0 \frac{\lambda^j}{\mu^j j!} \end{aligned}$$

avec

$$\pi_0 \left( 1 + \sum_{j=1}^{+\infty} \frac{\lambda^j}{\mu^j j!} \right) = 1$$

On reconnaît le développement en série entière de $e^x = \sum_{j=0}^{+\infty} \frac{x^j}{j!}$ en $x = \frac{\lambda}{\mu}$. On trouve donc

$$\pi_0 = e^{-\frac{\lambda}{\mu}}$$

D'où, finalement,

$$\forall j \in \mathbb{N} \quad \pi_j = e^{-\frac{\lambda}{\mu}} \left( \frac{\lambda}{\mu} \right)^j \frac{1}{j!}$$

Par conséquent la v.a. $N_\infty$, égale au nombre de clients à un instant quelconque du régime stationnaire, suit la [[Loi de Poisson|loi de Poisson]] de paramètre $\frac{\lambda}{\mu}$. Le nombre moyen de clients dans le système en régime stationnaire est donc

$$\overline{N} = \mathbb{E}(N_\infty) = \frac{\lambda}{\mu}$$

Avec la [[Formule de Little]] on en déduit le temps moyen passé par un client dans le système en régime stationnaire :

$$\overline{R} = \frac{\overline{N}}{\overline{\lambda}} = \frac{\overline{N}}{\lambda} = \frac{1}{\mu}$$

# Remarque

1. Le paramètre $\frac{\lambda}{\mu}$ ne représente plus, comme dans la [[File M-M-1|M/M/1]], l'intensité du trafic. En effet $\lambda$ est bien le nombre moyen d'arrivées par unité de temps, mais $\mu$ n'est pas le nombre moyen de clients servis par unité de temps : puisque $\overline{R} = \frac{1}{\mu}$, $\mu$ représente le nombre de clients qu'*un des serveurs* peut traiter en une unité de temps, mais l'ensemble du système peut en théorie traiter une infinité de clients par unité de temps.

   Une quantité plus intéressante dans ce contexte est la **probabilité d'occupation du système**, qui représente la fraction de temps pendant laquelle au moins un des serveurs est occupé (en régime stationnaire), c'est-à-dire le taux d'activité global du système :

   $$1 - \pi_0 = 1 - e^{-\frac{\lambda}{\mu}}$$

2. Le développement en série entière de $e^x$ converge pour toute valeur de $x$ : il n'y a donc pas de condition d'existence du régime stationnaire. C'est une différence fondamentale avec la file $M/M/n$. C'était prévisible : puisqu'il n'y a aucune attente, le nombre de clients ne peut pas « exploser » et ce système d'attente possède donc toujours un régime stationnaire (il ne peut pas « saturer »).

3. Pour ce modèle sans attente, $\overline{R} = \frac{1}{\mu}$ représente aussi bien le temps moyen passé dans le système en régime stationnaire que la durée moyenne de service d'un client quelconque.

4. La condition de la distribution limite porte sur l'indice $j$ de $\pi_j$ (c'est bien $j \geq 1$ que l'on doit écrire) et non sur $k$, qui n'est que l'indice muet du produit $\prod_{k=1}^{j}$ : la confusion entre les deux indices est fréquente.

# Liens avec d'autres lois

La file $M/M/\infty$ est un cas particulier du [[Processus de naissance et de mort]], de taux de transition $\lambda(k) = \lambda$ et $\mu(k) = k\mu$ ; elle sert également d'approximation à la [[File M-M-n-K|M/M/n/K]] lorsque le nombre de serveurs est grand.

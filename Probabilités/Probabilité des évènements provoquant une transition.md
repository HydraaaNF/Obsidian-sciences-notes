# Définition

On considère une [[File d'attente|file d'attente]] à $n$ serveurs identiques montés en parallèle, où $N(t)$ désigne le nombre de clients présents dans la file à l'instant $t$, et telle que :

- les arrivées se font suivant un [[Processus de Poisson|processus de Poisson]] de taux $\lambda$ ;
- la durée de service suit la [[Loi exponentielle|loi exponentielle]] $\mathcal{E}(\mu)$.

Soient $(k, \ell) \in \mathbb{N}^2$ et $E_{k, \ell}$ l'évènement « entre $t$ et $t + \delta t$, on constate exactement $k$ fins de service parmi les clients en service à l'instant $t$ et exactement $\ell$ nouvelles arrivées ».

On appelle **évènements provoquant une transition** (**EPT**) de l'état $i$ à l'état $j$ pendant une durée $\delta t$ les évènements disjoints deux à deux qui provoquent une transition de $i$ vers $j$ pendant cette durée.

# Théorèmes

**Probabilité des évènements provoquant les transitions.** Si $i \leq n$ et $k \leq i$, alors

$$\mathbb{P}(E_{k,\ell} \mid N(t) = i) = \binom{i}{k} (1 - e^{-\mu \delta t})^k e^{-\mu(i-k)\delta t} e^{-\lambda \delta t} \frac{(\lambda \delta t)^\ell}{\ell!}$$

Si $i \geq n$ et $k \leq n$, alors

$$\mathbb{P}(E_{k,\ell} \mid N(t) = i) = \binom{n}{k} (1 - e^{-\mu \delta t})^k e^{-\mu(n-k)\delta t} e^{-\lambda \delta t} \frac{(\lambda \delta t)^\ell}{\ell!}$$

### Démonstration

La probabilité qu'un client déjà en service à $t$ termine son service entre $t$ et $t+\delta t$ est égale à la probabilité que son **temps résiduel de service** soit inférieur à $\delta t$. Comme la loi $\mathcal{E}(\mu)$ est **sans mémoire**, c'est

$$\mathbb{P}(S \leq \delta t) = \int_0^{\delta t} \mu e^{-\mu s}\,ds = 1 - e^{-\mu \delta t}$$

Interprétons une fin de service entre $t$ et $t+\delta t$ comme un « succès ». En vertu de l'indépendance des temps de service entre eux, le nombre de fins de service avant $t+\delta t$ parmi les clients en service à l'instant $t$ est une [[Loi binomiale|v.a. binomiale]] de paramètres $i$ et $1 - e^{-\mu \delta t}$ si $i \leq n$ (car dans ce cas, à l'instant $t$ les $i$ clients sont en service), de paramètres $n$ et $1 - e^{-\mu \delta t}$ si $i \geq n$ (car dans ce cas, à l'instant $t$ il y a $n$ clients en service, ainsi que $i-n$ dans la zone d'attente qui n'influent pas sur le calcul de $\mathbb{P}(E_{k,\ell} \mid N(t) = i)$).

Par ailleurs, la probabilité de $\ell$ nouvelles arrivées entre $t$ et $t+\delta t$ est, d'après la [[Loi du processus de Poisson|loi du processus de Poisson]],

$$e^{-\lambda \delta t} \frac{(\lambda \delta t)^{\ell}}{\ell!}$$

Grâce à l'[[Indépendance de variables aléatoires|indépendance]] des durées de service et des temps d'inter-arrivées, on obtient les deux expressions ci-dessus.

**Développement limité de la probabilité des EPT.** Sous les hypothèses précédentes, quand $\delta t$ tend vers $0$,

$$\mathbb{P}(E_{k,\ell} \mid N(t)=i)=
\begin{cases}
\binom{i}{k}\dfrac{\mu^k\lambda^\ell}{\ell!}(\delta t)^{k+\ell}+o\!\left((\delta t)^{k+\ell}\right) & \text{si } i\leq n \text{ et } k\leq i \\
\binom{n}{k}\dfrac{\mu^k\lambda^\ell}{\ell!}(\delta t)^{k+\ell}+o\!\left((\delta t)^{k+\ell}\right) & \text{si } i\geq n \text{ et } k\leq n
\end{cases}
$$

En particulier, dès que $k+\ell\geq 2$, les évènements $E_{k,\ell}$ ont une probabilité négligeable devant $\delta t$.

# Interprétation

Lorsque l'on cherche les taux de transition $a_{i,j}$ d'une [[Chaîne de Markov à temps continu|chaîne de Markov à temps continu]], on doit trouver un développement limité au voisinage de $0$ de $p_{i,j}(\delta t)$. Parmi tous les EPT de l'état $i$ à l'état $j$ pendant une durée $\delta t$, il suffit de considérer un développement limité de la somme des probabilités des évènements dont la probabilité a l'ordre de grandeur le plus grand au voisinage de $0$.

Or les différents EPT sont soit un évènement du type $E_{k,\ell}$, soit de probabilité négligeable devant celle d'un évènement $E_{k,\ell}$. Il suffit donc en pratique de connaître un développement limité des $\mathbb{P}(E_{k,\ell} \mid N(t) = i)$ : c'est l'objet du développement limité ci-dessous.

# Exemple

Considérons le cas de $n = 2$ serveurs et supposons qu'à l'instant $t$ il y a un seul client ($i = 1$) ; ce client est donc en service à $t$. Considérons alors l'évènement suivant : « entre $t$ et $t + \delta t$ le client en service à $t$ termine son service, un autre client arrive (dont le service commence immédiatement puisqu'il y a soit un, soit deux serveurs libres suivant qu'il est arrivé avant ou après la fin de service du premier client) et ce deuxième client termine lui aussi son service avant $t + \delta t$ ». Cette situation ne correspond ni à l'évènement $E_{1,1}$, ni à l'évènement $E_{2,1}$ puisque le deuxième client n'était pas en service à l'instant $t$. Cet évènement est non seulement inclus dans $E_{1,1}$, mais il a en fait une probabilité d'ordre de grandeur $\mathcal{O}((\delta t)^3)$, donc négligeable devant celle de $E_{1,1}$ (qui est un $\mathcal{O}((\delta t)^2)$), donc on peut ne pas en tenir compte dans le calcul des $p_{1,j}$.

# Remarque

Le développement limité de la probabilité des EPT s'utilise lors de l'étude des files [[File M-M-1|M/M/1]], M/M/n, [[File M-M-infini|M/M/∞]] et [[File M-M-n-K|M/M/n/K]].

# Définition

Un processus stochastique à temps continu $(N(t))_{t \geq 0}$, à valeurs dans un espace d'états $E$ (ensemble fini ou dénombrable), est une **chaîne de Markov à temps continu homogène** (CMTCH) lorsque la connaissance de sa trajectoire passée (les valeurs de $N(u)$ pour $u < s$) n'apporte aucune information sur la loi de son état futur, et que la quantité suivante ne dépend pas de $s$ :

$$p_{i,j}(t) = \mathbb{P}(N(s+t) = j \mid N(s) = i)$$

La fonction $p_{i,j} : t \mapsto p_{i,j}(t)$ est appelée **fonction probabilité de transition** de l'état $i$ vers l'état $j$.

Les files markoviennes, c'est-à-dire les [[File d'attente|systèmes d'attente]] « sans mémoire » dont font partie les files de la forme $M/M/\dots$ (voir la [[Nomenclature de Kendall]] pour cette notation), en constituent le cadre d'application : les [[Temps d'inter-arrivée d'un processus de Poisson|temps d'inter-arrivées]] y sont indépendants et de même loi [[Loi exponentielle|exponentielle]], et les durées de service sont indépendantes et de même loi exponentielle. Le processus des arrivées est alors un [[Processus de Poisson]], dont le taux $\lambda$ est le nombre moyen d'arrivées par unité de temps : comme $A(t) \sim \mathcal{P}(\lambda t)$, on a $\mathbb{E}(A(1)) = \lambda$, et la durée moyenne entre deux arrivées est $\mathbb{E}(X_n) = \frac{1}{\lambda}$, puisque $X_n \sim \mathcal{E}(\lambda)$. On admet que si la loi des temps d'inter-arrivées et celle des temps de service sont toutes deux **sans mémoire**, le processus $(N(t))_{t \geq 0}$ égal au [[Processus d'arrivée et de service|nombre de clients présents]] dans le système d'attente (dans la zone d'attente ou dans l'un des serveurs) est une CMTCH.

# Propriétés

On admet les notions suivantes sur les CMTCH.

**Processus standard.** On suppose que les fonctions $p_{i,j}$ vérifient l'hypothèse suivante, naturelle dans les applications :

$$\text{Si } i \neq j \text{ alors } \lim_{t \to 0^+} p_{i,j}(t) = 0$$

$$\lim_{t \to 0^+} p_{i,i}(t) = 1$$

Le processus de Markov est alors dit **standard**. Sous cette condition, les fonctions $p_{i,j}$ sont dérivables sur $\mathbb{R}^+$ et admettent un développement limité d'ordre 1 en $0$ :

$$\text{Si } i \neq j \text{ alors } p_{i,j}(t) = a_{i,j}t + o(t)$$

$$p_{i,i}(t) = 1 + a_{i,i}t + o(t)$$

où l'on a posé $a_{i,j} = p'_{i,j}(0)$, en utilisant $p_{i,j}(0) = 0$ lorsque $i \neq j$ et $p_{i,i}(0) = 1$.

**Taux de transition instantané.** Pour $j \neq i$, le réel positif $a_{i,j}$ est le **taux de transition instantané de l'état $i$ à l'état $j$**, et $a_i = -a_{i,i}$ est le **taux instantané de départ de l'état $i$**. On a

$$a_{i,i} = - \sum_{j \neq i} a_{i,j} \leq 0$$

c'est-à-dire $a_i = \sum_{k \neq i} a_{i,k} \geq 0$.

**Temps d'atteinte d'un état.** Pour un couple d'états $(i,j)$ avec $j \neq i$ et $a_{i,j} \neq 0$, conditionnellement à $N(s) = i$, le temps d'atteinte de l'état $j$, compté à partir de l'instant $s$, **n'est pas exponentiel en général**. En définissant

$$T_{j,s} = \inf\{t > 0 \mid N(s+t) = j\}$$

l'exponentielle de taux $a_{i,j}$ ne décrit que la **durée de la transition directe** de $i$ vers $j$ : chaque destination possible $j$ depuis $i$ est munie d'une horloge exponentielle indépendante de taux $a_{i,j}$, et en notant $\tau_{i,j}$ cette durée,

$$\mathbb{P}(\tau_{i,j} > t \mid N(s) = i) = e^{-a_{i,j}t}$$

Le temps moyen de la transition directe de $i$ vers $j$ est donc $\frac{1}{a_{i,j}}$. Le temps d'atteinte $T_{j,s}$ coïncide avec cette durée, et suit donc la loi $\mathcal{E}(a_{i,j})$, lorsque $j$ est la seule destination possible depuis $i$ (auquel cas $a_i = a_{i,j}$) ; en présence d'autres destinations possibles, sa loi n'est pas exponentielle en général et dépend de l'ensemble des chemins menant de $i$ à $j$. Le seul temps exponentiel en toute généralité est le **temps de séjour** $S_{i,s} \sim \mathcal{E}(a_i)$ (voir ci-dessous).

**Choix de l'état de destination.** Sachant que la chaîne quitte l'état $i$, elle transite vers l'état $j$ avec la probabilité

$$q_{i,j} = \frac{a_{i,j}}{\sum_{k \neq i} a_{i,k}}$$

**Temps de séjour dans un état.** Si l'on note $a_i = \sum_{k \neq i} a_{i,k}$, alors partant de $i$ à l'instant $s$, le temps de séjour dans l'état $i$ suit une loi $\mathcal{E}(a_i)$. Autrement dit, en définissant

$$S_{i,s} = \inf\{t > 0 \mid N(s+t) \neq i\}$$

on a

$$\mathbb{P}(S_{i,s} > t \mid N(s) = i) = e^{-a_i t}$$

**Détermination pratique des taux.** Le plus naturel pour déterminer les taux $a_{i,j}$ est de calculer un **développement limité de $p_{i,j}(t)$ d'ordre 1 au voisinage de $0$**. Pour représenter graphiquement une CMTCH, on construit un **graphe valué** dont les nœuds sont les états (les valeurs entières pouvant être prises par $N(t)$) et dont les poids sont les taux de transition instantanés $a_{i,j}$, pour $i \neq j$.

# Interprétation

- L'hypothèse « standard » revient à dire que, **pour $t$ petit**, la probabilité de transiter de $i$ vers $j$ pendant une durée $t$ est **approximativement proportionnelle** à la durée $t$, le coefficient de proportionnalité étant justement le taux de transition $a_{i,j}$.
- Pour $j \neq i$, le taux $a_{i,j}$ représente la « **rapidité moyenne** » avec laquelle le processus peut transiter de l'état $i$ à l'état $j$ : si chaque fois qu'on atteint $j$, on remet le processus dans l'état $i$, on observera **en moyenne** $a_{i,j}$ **transitions de $i$ vers $j$ en une unité de temps**.
- Partant de $i$, la chaîne peut en général transiter vers plusieurs états, avec des rapidités $a_{i,j}$ potentiellement différentes : si $a_{i,j} > a_{i,k} > 0$, alors en pratique, partant de $i$, elle transitera plus souvent vers $j$ que vers $k$. La destination est choisie avec une probabilité proportionnelle au taux de transition correspondant.

# Remarque

Le temps d'atteinte de l'état $j$ partant de $i$ n'est pas exponentiel en général ; l'exponentielle de taux $a_{i,j}$ ne décrit que la durée de la transition directe de $i$ vers $j$, le seul temps exponentiel en toute généralité étant le temps de séjour $S_{i,s} \sim \mathcal{E}(a_i)$.

Voir le [[Processus de naissance et de mort]] et la [[File M-M-1]] pour l'étude des files markoviennes fondées sur ces taux de transition.

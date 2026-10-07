# Définition

Une **file à pertes** $M/M/n/K$ (voir la [[Nomenclature de Kendall]]) est un [[File d'attente|système d'attente]] composé d'une zone d'attente ayant un nombre limité de places et d'une zone de service avec $n$ serveurs montés en parallèle et indépendants entre eux. La capacité totale de ce système est $K \geq n$ (il y a donc $K - n$ places dans la zone d'attente, et il y a une probabilité non nulle de perdre des clients).

Le flux des arrivées se fait suivant un [[Processus de Poisson]] de taux $\lambda$. Les durées de service sont, quel que soit le serveur occupé, des variables aléatoires indépendantes et de même loi $\mathcal{E}(\mu)$, et elles sont supposées indépendantes des temps d'inter-arrivées.

On note $(N(t))_{t \geq 0}$ le processus stochastique représentant le nombre de clients dans le système à l'instant $t$. C'est une [[Chaîne de Markov à temps continu|CMTC]] homogène et standard ; ici, l'espace des états est fini :

$$E = \{0, 1, \dots, K\}$$

# Propriétés

## Taux de transition

Une adaptation du raisonnement utilisé pour déterminer les taux de transition de la file $M/M/n$ (voir [[Probabilité des évènements provoquant une transition]]) montre que $(N(t))_{t \geq 0}$ est un [[Processus de naissance et de mort|processus de naissance et de mort]] (PNM) de taux de transition :

$$\forall i \in \{0, 1, \dots, K-1\} \qquad \lambda(i) = \lambda$$

$$\forall i \in \{1, \dots, n\} \qquad \mu(i) = i\mu$$

$$\forall i \in \{n+1, \dots, K\} \qquad \mu(i) = n\mu$$

## Régime stationnaire

On cherche un éventuel [[Système ergodique|régime stationnaire]] en résolvant le système d'équations donné par les équations de balance (cas d'un PNM à espace d'états fini), avec la condition de normalisation $\sum_{j=0}^{K} \pi_j = 1$. On trouve :

$$\forall j \in \{0, \dots, n\}, \qquad \pi_j = \pi_0 \frac{1}{j!}\left(\frac{\lambda}{\mu}\right)^j$$

$$\forall j \in \{n+1, \dots, K\} \qquad \pi_j = \pi_0 \frac{1}{n!n^{j-n}}\left(\frac{\lambda}{\mu}\right)^j$$

où la **probabilité d'inoccupation** du système $\pi_0$ est obtenue en utilisant la condition de normalisation.

## Probabilité de blocage et moyennes

La **probabilité de blocage** du système est la probabilité qu'un client qui arrive en régime stationnaire soit refusé à l'entrée : c'est la probabilité de trouver le système dans l'état $K$ quand on arrive en régime stationnaire. C'est donc :

$$\pi_K = \pi_0 \frac{n^n}{n!}\left(\frac{\lambda}{n\mu}\right)^K = \pi_0 \frac{n^n}{n!} \rho^K$$

où l'on note $\rho = \frac{\lambda}{n\mu}$.

Avec cette valeur, le taux moyen des arrivées en régime stationnaire est :

$$\bar{\lambda} = \sum_j \lambda(j)\pi_j = \sum_{j=0}^{K-1} \lambda \pi_j = \lambda(1 - \pi_K)$$

Le nombre moyen de clients en régime stationnaire est :

$$\bar{N} = \sum_{j=1}^{K} j\pi_j$$

Tenant compte des valeurs des $\pi_j$, c'est un calcul fastidieux dans le cas général, mais sans réelle difficulté. Dans le cas particulier du **système sans attente possible** $M/M/n/n$ (c'est-à-dire $K = n$), le temps de séjour $\bar{R}$ d'un client non refusé est égal à son temps de service $\frac{1}{\mu}$ ; le nombre moyen de clients en régime stationnaire s'obtient alors simplement avec la [[Formule de Little|formule de Little]] :

$$\bar{N} = \bar{\lambda} \times \bar{R} = \frac{\lambda}{\mu}(1 - \pi_n)$$

# Remarque

1. Il existe toujours un régime stationnaire (pour toutes valeurs de $\lambda$ et de $\mu$), ce qui est logique puisque $E$ est fini, contrairement à la [[File M-M-1]], dont le régime stationnaire n'existe que sous la condition $\lambda < \mu$.

2. Pour la file à capacité illimitée $M/M/n$, le paramètre $\rho = \frac{\lambda}{n\mu}$ représente l'**intensité globale de trafic** : $\lambda$ est alors le nombre moyen d'arrivées par unité de temps et $n\mu$ le nombre moyen de clients que le système peut traiter par unité de temps. Ce n'est plus vrai pour la file à capacité limitée $M/M/n/K$, car ici le nombre moyen d'arrivées par unité de temps est $\bar{\lambda} = \lambda(1 - \pi_K)$.

3. Bien entendu, on peut écrire toutes les formules en fonction de $\pi_K$ plutôt qu'en fonction de $\pi_0$.

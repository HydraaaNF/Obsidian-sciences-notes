# Loi

Un [[Champ aléatoire de Markov|champ aléatoire]] $X$ est indexé par un ensemble fini de sites $S$ : pour tout site $s \in S$, la variable $X_s$ prend ses valeurs dans un ensemble $E$, et une configuration du champ est un vecteur $x = (x_s)_{s \in S}$ de l'espace d'échantillonnage

$$\Omega = E^{|S|}$$

Le [[Graphes dirigés et graphes non dirigés|graphe non dirigé]] du champ munit $S$ d'un système de voisinage $V$, qui associe à chaque site $s$ l'ensemble $V_s$ de ses voisins ; on note $\mathcal{C}$ l'ensemble des cliques de ce système, c'est-à-dire des parties de $S$ dont deux sites quelconques sont voisins.

La **distribution de Gibbs** d'énergie $U$ est la loi sur $\Omega$ définie par

$$\mathbb{P}[X = x] = \frac{1}{Z} \exp\left(-\underbrace{\sum_{c \in \mathcal{C}} U_c(x)}_{U(x)}\right)$$

Chaque $U_c$ est le potentiel de la clique $c$ : une fonction qui ne dépend que des variables $x_s$ des sites $s \in c$. La somme des potentiels est l'énergie de la configuration,

$$U(x) = \sum_{c \in \mathcal{C}} U_c(x)$$

et la constante de normalisation $Z$ vaut

$$Z = \sum_{x \in \Omega} \exp\left(-U(x)\right)$$

# Interprétation

Le terme $\exp(-U(x))$ est le poids de la configuration $x$ : plus son énergie $U(x)$ est faible, plus la configuration est probable, et sa probabilité décroît de façon exponentielle quand $U(x)$ croît. L'énergie mesure donc le coût de la configuration, et les configurations les plus probables sont celles d'énergie minimale.

Chaque potentiel $U_c$ ne porte que sur les sites d'une clique, c'est-à-dire sur un groupe de sites mutuellement voisins : il encode une interaction locale entre ces sites. Un potentiel qui décroît lorsque les sites de la clique prennent une certaine configuration favorise cette configuration, un potentiel qui croît la défavorise.

La constante $Z$ ne dépend pas de $x$ : elle somme les poids de toutes les configurations de $\Omega$ et ramène la loi à une masse totale de $1$. L'espace $\Omega$ étant fini, cette somme est finie.

# Propriétés

La constante $Z$ normalise bien la loi :

$$\sum_{x \in \Omega} \mathbb{P}[X = x] = \frac{1}{Z} \sum_{x \in \Omega} \exp\left(-U(x)\right) = 1 .$$

L'exponentielle d'une somme étant le produit des exponentielles, la distribution de Gibbs se factorise sur les cliques :

$$\mathbb{P}[X = x] = \frac{1}{Z} \prod_{c \in \mathcal{C}} \exp\left(-U_c(x)\right).$$

Chaque facteur ne dépend que des sites de sa clique : une distribution de Gibbs est donc un [[Graphe de facteurs]] particulier, dont les facteurs sont indexés par les cliques du système de voisinage, avec $\psi_c = \exp(-U_c)$.

Si tous les potentiels sont nuls, l'énergie est identiquement nulle, $Z = |\Omega|$ et la loi se réduit à la loi uniforme sur les configurations, celle d'[[Entropie d'une variable aléatoire discrète|entropie]] maximale en l'absence d'interaction.

L'énergie n'est définie qu'à une constante additive près : en remplaçant $U$ par $U + k$, la constante de normalisation est multipliée par $e^{-k}$ et la loi reste inchangée, puisque

$$\frac{\exp\left(-U(x) - k\right)}{\sum_{x' \in \Omega} \exp\left(-U(x') - k\right)} = \frac{\exp\left(-U(x)\right)}{\sum_{x' \in \Omega} \exp\left(-U(x')\right)} .$$

# Remarque

Le potentiel d'une clique s'écrit de façon équivalente comme l'exponentielle de son énergie :

$$\psi_c(x_c) = \exp\left(-U_c(x_c)\right)$$

où $x_c$ désigne les coordonnées de $x$ sur la clique $c$. L'écriture $\exp\left(-\sum_c U_c(x)\right)$ de la loi, celle en produit de potentiels $\prod_c \psi_c(x_c)$ et celle en facteurs $f_i$ du [[Graphe de facteurs]] désignent le même objet : seule change la notation. Le passage de la somme des énergies au produit des potentiels utilise l'identité $\exp(a+b) = \exp(a)\exp(b)$.

La distribution de Gibbs est la loi associée à un [[Champ aléatoire de Markov]] : les deux descriptions coïncident, toute loi strictement positive vérifiant la propriété de Markov relativement à $V$ étant une distribution de Gibbs dont les potentiels sont indexés par les cliques de $V$, et réciproquement.

La forme obtenue, une exponentielle d'une somme de termes locaux divisée par une constante de normalisation, est celle d'une [[Forme exponentielle d'une distribution de maximum d'entropie|distribution de maximum d'entropie]] et d'un [[Modèle log-linéaire conditionnel]] : ces deux familles de lois sont des cas particuliers de distributions de Gibbs, dont l'énergie est une combinaison linéaire de fonctions de traits.

Conditionnellement à des observations, la loi a posteriori d'un [[Champ de Markov caché]] est encore une distribution de Gibbs, d'énergie obtenue en ajoutant à celle du champ une énergie qui mesure l'adéquation des observations à la configuration.

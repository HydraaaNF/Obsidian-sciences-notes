# Loi

On considère un ensemble fini de sites $S$ ; chaque site $s \in S$ porte une variable $X_s$ à valeurs dans un ensemble $E$. Une configuration du champ est un vecteur $x = (x_s)_{s \in S}$ de l'espace

$$\Omega = E^{|S|}$$

Le [[Graphes dirigés et graphes non dirigés|graphe non dirigé]] du champ munit $S$ d'un système de voisinage $V$ ; on note $\mathcal{C}$ l'ensemble de ses cliques, c'est-à-dire des ensembles de sites deux à deux voisins.

La **distribution de Gibbs** est la loi sur $\Omega$ associée à un [[Champ aléatoire de Markov]], définie par

$$\mathbb{P}[X = x] = \frac{1}{Z} \exp\left(-\underbrace{\sum_{c \in \mathcal{C}} U_c(x)}_{U(x)}\right)$$

Chaque $U_c$ est le potentiel de la clique $c$ : une fonction qui ne dépend que des variables $x_s$ des sites $s \in c$. La somme des potentiels est l'énergie de la configuration,

$$U(x) = \sum_{c \in \mathcal{C}} U_c(x)$$

et la constante de normalisation $Z$ vaut

$$Z = \sum_{x \in \Omega} \exp\left(-U(x)\right)$$

La loi s'écrit ainsi avec l'énergie seule :

$$\mathbb{P}[X = x] = \frac{1}{Z} \exp\left(-U(x)\right)$$

# Interprétation

Le terme $\exp(-U(x))$ est le poids de la configuration $x$ : plus son énergie $U(x)$ est faible, plus la configuration est probable, et sa probabilité décroît de façon exponentielle quand $U(x)$ croît. L'énergie est une somme de contributions locales, une par clique ; deux sites qui n'appartiennent à aucune clique commune n'interagissent pas directement dans la loi.

La constante $Z$ ne dépend pas de $x$ : elle somme les poids de toutes les configurations de $\Omega$ et ramène la loi à une masse totale de $1$, c'est-à-dire $\sum_{x \in \Omega} \mathbb{P}[X = x] = 1$. L'espace $\Omega$ étant fini, cette somme est finie.

# Remarque

Le potentiel d'une clique s'écrit de façon équivalente comme l'exponentielle de son énergie :

$$\psi_c(x_c) = \exp\left(-U_c(x_c)\right)$$

où $x_c$ désigne les coordonnées de $x$ sur la clique $c$. L'écriture $\exp\left(-\sum_c U_c(x)\right)$ de la loi, celle en produit de potentiels $\prod_c \psi_c(x_c)$ et celle en facteurs $f_i$ du [[Graphe de facteurs]] désignent le même objet : seule change la notation. Le passage de la somme des énergies au produit des potentiels utilise l'identité $\exp(a+b) = \exp(a)\exp(b)$.

La propriété de Markov locale qui caractérise le champ auquel cette loi est associée est formulée dans [[Champ aléatoire de Markov]].

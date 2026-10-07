# Loi

La **distribution de Gibbs** est la loi associée à un [[Champ aléatoire de Markov]] : pour une configuration $x \in \Omega = E^{|S|}$ du champ, elle s'écrit

$$\mathbb{P}[X = x] = \frac{1}{Z}\exp\!\left(-\underbrace{\sum_{c \in \mathcal{C}} U_c(x)}_{U(x)}\right)$$

$$Z = \sum_{x \in \Omega} \exp\!\left(-U(x)\right)$$

où $\mathcal{C}$ est l'ensemble des cliques du champ, $U(x) = \sum_{c \in \mathcal{C}} U_c(x)$ la somme des termes associés à ces cliques, et $Z$ la constante de normalisation.

# Interprétation

La probabilité d'une configuration $x$ décroît de façon exponentielle avec $U(x)$ : plus $U(x)$ est grand, plus la configuration est improbable. La constante $Z$, qui ne dépend pas de $x$, normalise la loi : $\sum_{x \in \Omega} \mathbb{P}[X = x] = 1$.

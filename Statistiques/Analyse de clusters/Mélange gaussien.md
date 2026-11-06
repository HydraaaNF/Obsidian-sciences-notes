# Définition

Un **mélange gaussien** est un [[Modèles de mélange|modèle de mélange]] dont chaque composante $f_i$ est la [[Densité d'un vecteur gaussien|densité]] d'un [[Vecteur gaussien]] de moyenne $\mu_i$ et de [[Matrice de covariance|matrice de covariance]] $\Sigma_i$ :

$$f_i(x) = \frac{1}{(2\pi)^{n/2} |\Sigma_i|^{1/2}} \exp \left\{ -\frac{1}{2} (x - \mu_i)^\top \Sigma_i^{-1} (x - \mu_i) \right\}$$

Les paramètres du modèle sont :

- les poids de chaque composante ($K$) ;
- les vecteurs des moyennes ($Kn$) ;
- les matrices de covariance ($Kn(n+1)/2$).

# Interprétation

Chaque composante $f_i$ est une densité gaussienne multivariée, dont les lignes de niveau sont des [[Ellipsoïdes d'isodensité]].

# Remarque

En pratique, on suppose souvent des matrices de covariance diagonales :

- beaucoup moins de paramètres ($Kn \ll Kn(n+1)/2$) ;
- beaucoup moins de calcul (évite l'inversion matricielle) ;
- la restriction peut être compensée par un plus grand nombre de composantes.

Pour l'estimation des paramètres, voir l'[[Espérance-maximisation pour un mélange de gaussiennes]].

# Liens avec d'autres lois

- La loi du mélange est la loi d'une variable aléatoire dont la composante est tirée par une [[Variables cachées d'un modèle de mélange|variable cachée]] : si $Z$ suit la loi des poids $(w_1, \dots, w_K)$ sur $\{1, \dots, K\}$ et si la loi de $X$ conditionnellement à $Z = i$ est la gaussienne de densité $f_i$, alors $X$ a pour densité $\sum_{i=1}^{K} w_i f_i(x)$.

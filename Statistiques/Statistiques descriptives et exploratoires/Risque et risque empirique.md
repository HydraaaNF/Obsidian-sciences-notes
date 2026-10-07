# Définition

Pour une fonction $f$ de l'[[Espace d'hypothèses]] $\mathcal{F}$, le risque espéré est défini par

$$R(f) = \mathbb{E}_Z[L(z, f)] = \int_Z L(z, f)p(z)dz$$

où $L$ est la [[Fonction de perte]] et $p(z)$ la loi des données.

Sur un échantillon $D_n$ de $n$ données $z_1, \dots, z_n$, le risque empirique est la moyenne des pertes sur ces données :

$$\hat{R}(f, D_n) = \frac{1}{n} \sum_{i=1}^n L(z_i, f)$$

# Interprétation

Le principe d'induction consiste à chercher la fonction $f \in \mathcal{F}$ qui minimise le risque espéré $R(f)$. Il se heurte à deux obstacles : la loi $p(z)$ des données est inconnue et on n'a pas accès à tous les $L(z, f)$.

On remplace alors le risque par le risque empirique et on minimise ce dernier, ce qui définit la solution

$$f^*(D_n) = \arg\min_{f \in \mathcal{F}} \hat{R}(f, D_n)$$

du [[Principe de minimisation du risque empirique]].

# Propriétés

Le risque empirique est un [[Biais d'un estimateur|estimateur sans biais]] du risque :

$$\mathbb{E}_{D_n}[\hat{R}(f, D_n)] = R(f)$$

L'erreur d'entraînement évalue le risque empirique en la solution $f^*(D_n)$ :

$$\hat{R}(f^*(D_n), D_n) = \min_{f \in \mathcal{F}} \hat{R}(f, D_n)$$

C'est en revanche une estimation biaisée du risque :

$$\mathbb{E}[R(f^*(D_n)) - \hat{R}(f^*(D_n), D_n)] \geq 0$$

En moyenne, l'erreur d'entraînement sous-estime donc le risque.

La solution $f^*(D_n)$ trouvée en minimisant l'erreur d'entraînement est meilleure sur $D_n$ que sur tout autre ensemble $D'_n$ tiré de $p(z)$.

# Remarque

L'erreur d'entraînement ne peut pas servir d'estimation directe du risque : elle est mesurée sur l'échantillon $D_n$ qui a servi à choisir $f^*(D_n)$ et sous-estime donc le risque ; estimer celui-ci correctement passe par une [[Estimation non biaisée du risque|estimation non biaisée du risque]].

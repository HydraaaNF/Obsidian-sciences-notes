# Définition

Le **principe de minimisation du risque empirique** (ERM, de l'anglais *empirical risk minimization*) consiste à choisir, dans l'[[Espace d'hypothèses|espace de fonctions]] $\mathcal{F}$, la fonction $f^*(D_n)$ qui minimise le [[Risque et risque empirique|risque empirique]] sur les données observées $D_n$ :

$$f^*(D_n) = \arg\min_{f \in \mathcal{F}} \hat{R}(f, D_n)$$

Le risque empirique est la moyenne de la [[Fonction de perte|perte]] sur les $n$ observations de l'échantillon :

$$\hat{R}(f, D_n) = \frac{1}{n} \sum_{i=1}^n L(z_i, f)$$

# Interprétation

Le risque empirique, construit sur les seules données observées, est un estimateur du [[Risque et risque empirique|risque]] :

$$R(f) = \mathbb{E}_Z[L(z, f)] = \int_Z L(z, f)p(z)dz$$

Minimiser le risque empirique revient donc à rechercher la fonction qui commet la plus faible perte moyenne sur l'échantillon $D_n$ ; la fonction retenue $f^*(D_n)$ dépend de cet échantillon.

# Remarque

L'estimation de la performance du modèle ainsi sélectionné relève de méthodes dédiées : l'[[Estimation non biaisée du risque]] et la [[Sélection de modèle et estimation de la performance]].

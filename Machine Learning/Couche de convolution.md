#ml-2

# Définition

Une couche de convolution applique des [[Filtre de convolution|filtres]] sur son entrée pour produire des [[Carte d'activation|cartes d'activation]] : chaque filtre balaie l'entrée et génère un [[Canal d'un tenseur|canal]] de sortie. Les canaux obtenus sont empilés, puis transmis aux couches suivantes jusqu'à la fonction de coût.

Un filtre est défini par ses [[Noyau de convolution|noyaux]] et un biais $b$, qui sont les paramètres apprenables de la couche. Sur une entrée à $N$ canaux, un filtre de taille $3 \times 3$ possède lui aussi $N$ canaux : il traverse l'épaisseur de l'entrée et produit un unique canal de sortie.

# Algorithme

Le calcul avant d'une couche de convolution s'enchaîne en quatre étapes :

| Étape | Élément | Rôle |
| --- | --- | --- |
| 1 | Entrée $3 \times 3 \times N$ | image, à $N$ canaux d'entrée |
| 2 | Filtres $3 \times 3 \times N$ | un filtre par canal de sortie |
| 3 | Convolution et activation | produit un canal de sortie par filtre |
| 4 | Empilement des canaux | assemble les canaux en une sortie multi-canaux |

La perte n'appartient pas à la couche : elle est calculée une seule fois pour le réseau, sur la sortie de la dernière couche comparée à la cible. Sa rétropropagation traverse ensuite toutes les couches et fournit à chacune le gradient de ses propres poids.

# Propriétés

À chaque mise à jour des paramètres, chaque poids $\omega_{i,j}$ d'un noyau est corrigé dans le sens opposé à la dérivée de la perte :

$$\omega_{i,j} \leftarrow \omega_{i,j} - \lambda \, \frac{\partial L}{\partial \omega_{i,j}}$$

avec :

- $\omega_{i,j}$ : poids du noyau,
- $\lambda$ : taux d'apprentissage (*learning rate*),
- $\dfrac{\partial L}{\partial \omega_{i,j}}$ : dérivée de la perte par rapport à ce poids.

# Remarque

La couche de convolution est la variante à poids partagés de la couche du [[Perceptron multicouche]] : un même noyau sert à toutes les positions qu'il balaie, au lieu d'avoir un poids propre par connexion.

Le [[Max pooling]] est le complément sans paramètre de la couche de convolution : il réduit la résolution des cartes d'activation produites.

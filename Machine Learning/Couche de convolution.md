#ml-2

# Définition

Une couche de convolution applique des **noyaux** sur son entrée pour produire des **cartes d'activation** : chaque noyau balaie l'entrée et génère un canal de sortie. Les canaux obtenus sont empilés, puis transmis aux couches suivantes jusqu'à la fonction de coût.

Un noyau est défini par ses poids et un biais $b$, qui sont les paramètres apprenables de la couche. Sur une entrée à $N$ canaux, un noyau de taille $3 \times 3$ possède lui aussi $N$ canaux : il traverse l'épaisseur de l'entrée et produit un unique canal de sortie.

# Algorithme

Le calcul d'une couche de convolution s'enchaîne en six étapes :

| Étape | Élément | Rôle |
| --- | --- | --- |
| 1 | Entrée $3 \times 3 \times N$ | image, à $N$ canaux d'entrée |
| 2 | Noyaux $3 \times 3 \times N$ | un noyau par canal de sortie |
| 3 | Convolution et activation | produit un canal de sortie par noyau |
| 4 | Empilement des canaux | assemble les canaux en une sortie multi-canaux |
| 5 | Perte | évalue la sortie par la fonction de coût $L$ |
| 6 | Rétropropagation | met à jour les poids |

# Propriétés

À la dernière étape, chaque poids $\omega_{i,j}$ du noyau est corrigé dans le sens opposé à la dérivée de la perte :

$$\omega_{i,j} \leftarrow \omega_{i,j} - \lambda \, \frac{\partial L}{\partial \omega_{i,j}}$$

avec :

- $\omega_{i,j}$ : poids du noyau,
- $\lambda$ : taux d'apprentissage (*learning rate*),
- $\dfrac{\partial L}{\partial \omega_{i,j}}$ : dérivée de la perte par rapport à ce poids.

# Remarque

La couche de convolution est la variante à poids partagés de la couche du [[Perceptron multicouche]] : un même noyau sert à toutes les positions qu'il balaie, au lieu d'avoir un poids propre par connexion.

L'étape de convolution se termine par une activation, qui rend la couche non linéaire : voir les [[Fonctions d'activation]].

Le calcul effectif du noyau sur une séquence est détaillé dans [[Convolution en une dimension]], sur une image dans [[Convolution en deux dimensions]].

La mise à jour des poids est une [[Descente de gradient]] appliquée aux paramètres du noyau, le gradient étant obtenu par [[Rétropropagation]] à travers la couche.

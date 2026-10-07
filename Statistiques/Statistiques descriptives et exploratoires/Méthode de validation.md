# Définition

La **méthode de validation** consiste à diviser les données en deux ensembles séparés.

# Algorithme

**Pour l'[[Estimation non biaisée du risque|estimation du risque]]**

- l'ensemble d'entraînement sert à la [[Sélection de modèle et estimation de la performance|sélection de modèle]] (éventuellement redécoupé en un ensemble d'entraînement et un ensemble de validation) ;
- l'ensemble de test sert à calculer le [[Risque et risque empirique|risque empirique]] comme estimation du risque.

**Pour la sélection de modèle**

- l'ensemble d'entraînement sert à estimer les paramètres avec des hyper-paramètres donnés ;
- l'ensemble de validation sert à estimer le risque empirique du modèle obtenu sur l'ensemble d'entraînement ;
- on sélectionne les hyper-paramètres donnant le meilleur risque empirique sur l'ensemble de validation ;
- on estime les paramètres du modèle sur l'ensemble complet des données pour les hyper-paramètres optimaux (facultatif).

# Remarque

Le risque sur l'ensemble de validation est un très mauvais estimateur du risque.

La [[Validation croisée]] généralise ce principe.

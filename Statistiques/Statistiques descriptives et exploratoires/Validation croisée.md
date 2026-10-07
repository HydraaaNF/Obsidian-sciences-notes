# Définition

La **validation croisée** consiste à diviser les données $D_n$ en $N$ ensembles séparés.

# Algorithme

**Pour l'[[Estimation non biaisée du risque|estimation du risque]]**

- pour chaque ensemble $D_i$ :
  - sélectionner le modèle sur l'**ensemble d'entraînement** $\{D_{j \neq i}\}$ ;
  - estimer le risque par le [[Risque et risque empirique|risque empirique]] sur l'**ensemble de test** $D_i$ ;
- moyenner les estimateurs de risque.

**Pour la [[Sélection de modèle et estimation de la performance|sélection de modèle]]**

- pour chaque ensemble $D_i$ :
  - sélectionner le meilleur modèle sur l'**ensemble d'entraînement** $\{D_{j \neq i}\}$, pour des hyper-paramètres donnés ;
  - calculer le risque empirique sur l'**ensemble de validation** $D_i$ ;
- sélectionner les hyper-paramètres donnant le meilleur risque empirique moyen sur tous les ensembles de validation ;
- estimer les paramètres du modèle sur l'ensemble complet des données, avec les paramètres optimaux.

# Remarque

La validation croisée généralise la [[Méthode de validation]].

# Définition

La sélection de modèle et l'estimation de la performance peuvent poursuivre trois objectifs :

1. donner le meilleur modèle possible sur un ensemble d'entraînement ;
2. donner la performance attendue d'un modèle obtenu par [[Risque et risque empirique|minimisation du risque empirique]] sur un ensemble d'entraînement ;
3. les deux à la fois : donner le meilleur modèle et sa performance attendue.

# Interprétation

Ces objectifs nécessitent toujours une estimation du risque :

$$\mathbb{E}_z[L(z, \hat{\theta})]$$

Estimer ce risque fait l'objet de méthodes dédiées : [[Estimation non biaisée du risque|estimation non biaisée du risque]], [[Méthode de validation]] et [[Validation croisée]].

#ml-1

# Définition

L'erreur d'un modèle de régression sur un [[Jeux d'entraînement, de développement et de test|jeu de test]] est la perte moyenne que le modèle commet sur les échantillons de ce jeu :

$$E(\text{modèle}, \text{test}) = \frac{1}{|\text{test}|} \sum_{(x_i, y_i) \in \text{test}} \mathcal{L}\left(y_i, \text{prédiction}(x_i, \text{modèle})\right)$$

où $x_i$ et $y_i$ sont la description et l'étiquette d'un échantillon, et $\mathcal{L}$ la [[Fonction de perte|fonction de perte]].

Avec $\hat{y}_i$ la prédiction du modèle sur l'échantillon $x_i$, les trois choix usuels sont les suivants.

**MAE** (erreur absolue moyenne) :

$$\text{MAE} = \frac{1}{n} \sum_i |y_i - \hat{y}_i|$$

**MSE** (erreur quadratique moyenne) :

$$\text{MSE} = \frac{1}{n} \sum_i (y_i - \hat{y}_i)^2$$

**RMSE** (racine de l'erreur quadratique moyenne) :

$$\text{RMSE} = \sqrt{\text{MSE}}$$

# Interprétation

- La MAE s'exprime dans la même unité que $y$ et résiste aux valeurs aberrantes.
- La MSE s'exprime dans l'unité de $y$ au carré et pénalise fortement les grosses erreurs.
- La RMSE revient à l'unité de $y$.
- Pour toutes ces mesures, une valeur plus basse est meilleure, 0 correspond à la prédiction parfaite, et il n'existe aucune borne supérieure.

# Remarque

- L'erreur moyenne sur un jeu de test est le [[Risque et risque empirique|risque empirique]] restreint à ce jeu : la moyenne des pertes $\mathcal{L}$ sur ses échantillons.
- La MAE moyenne les [[Écart absolu moyen|écarts absolus]] entre étiquette et prédiction, et la MSE moyenne leurs carrés.
- La MSE de prédiction ne doit pas être confondue avec l'[[Erreur quadratique moyenne]] d'un estimateur, qui mesure l'écart quadratique moyen entre un estimateur et le paramètre qu'il estime.
- Le [[Coefficient de détermination]] complète ces mesures pour un modèle de régression.
- Le choix de la perte $\mathcal{L}$ fixe la mesure d'erreur : MAE, MSE et RMSE en sont les choix usuels en régression.

#ml-1

# Définition

Soit $n$ observations d'une variable cible $y$, leurs prédictions $\hat{y}_i$ et la moyenne $\bar{y}$ des valeurs observées. Le **coefficient de détermination** $R^2$ rapporte l'erreur du modèle à celle d'une référence élémentaire, la *baseline* :

$$
R^2 = 1 - \frac{\sum_i (y_i - \hat{y}_i)^2}{\sum_i (y_i - \bar{y})^2} = 1 - \frac{\text{erreur du modèle}}{\text{erreur de la baseline}}
$$

La baseline retenue est la prédiction constante de la moyenne : un modèle qui prédit toujours $\bar{y}$ pour toute entrée.

# Interprétation

- $R^2 = 1$ : prédiction parfaite ;
- $R^2 = 0$ : pas mieux que prédire la moyenne ;
- $R^2 < 0$ : pire que la baseline, ce qui arrive effectivement.

Le coefficient de détermination est la seule lecture solide de la précision pour une régression.

# Remarque

Une valeur d'erreur isolée, par exemple $\text{RMSE} = 4.2$, n'est pas interprétable sans point de comparaison ; c'est la comparaison à la baseline qui donne son sens à la mesure, comme le fait $R^2$ pour les [[Mesures d'erreur en régression|mesures d'erreur en régression]].

Dans le cas d'un ajustement par la [[Droite de régression de y en x|droite de régression]], le coefficient de détermination coïncide avec le carré du [[Coefficient de corrélation linéaire|coefficient de corrélation linéaire]].

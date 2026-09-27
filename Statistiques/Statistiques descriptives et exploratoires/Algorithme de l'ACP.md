# Algorithme
Soit $X$ la matrice $n \times p$ des observations (on suppose les données centrées et de poids égal $1/n$).

1. Calculer la matrice de covariance $V_{p \times p} = \frac{1}{n}X^TX$ (ou la matrice de corrélation $R$)
2. Calculer le système propre $V_{p\times p} = U_{p\times p}\Lambda_{p\times p}U_{p\times p}^{-1} = U\Lambda U^T$
3. Trier les valeurs propres par ordre décroissant, ne garder que les plus grandes, et trier $U_{p\times p}$ en conséquence pour obtenir $U_{q\times p}$
4. Reconstruire ou projeter $X$ : $Y_{q\times n} = U_{q\times p}X_{p\times n}$

# Remarque
Pour des données de très grande dimension, l'étape 2 peut être remplacée par l'algorithme **NIPALS**, plus efficace que la diagonalisation directe.

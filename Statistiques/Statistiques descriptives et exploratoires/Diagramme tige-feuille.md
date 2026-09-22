# Définition
Représentation compacte d'une distribution de données numériques : chaque valeur est décomposée en une « tige » (les chiffres de poids fort, partagés entre plusieurs valeurs) et une « feuille » (le dernier chiffre), organisées en tableau.

# Interprétation
Combine les avantages d'un [[Histogramme]] (aperçu visuel de la distribution) et d'un tableau de données brutes (les valeurs individuelles restent lisibles).

# Exemple
| Tige | Feuilles |
|:---:|---|
| 2 | 1 4 8 |
| 3 | 0 2 2 5 7 9 |
| 4 | 1 3 3 4 6 8 9 |
| 5 | 0 2 5 7 |
| 6 | 1 4 |

*Lecture : la ligne `4 \| 3 3 4 6 8 9` représente les valeurs 43, 43, 44, 46, 48, 49.*

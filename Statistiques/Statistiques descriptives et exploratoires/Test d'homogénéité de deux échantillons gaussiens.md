# Définition

On effectue un **test d'homogénéité** dans le cas de deux [[Échantillon et échantillonnage|échantillons]] indépendants de [[Loi gaussienne|loi mère gaussienne]], afin de savoir si les lois mères associées sont identiques.

On suppose que :

- $(x_1, \dots, x_{n_1})$ est une observation de l'échantillon $(X_1, \dots, X_{n_1})$ de loi mère $\mathcal{N}(m_1, \sigma_1^2)$ ;
- $(y_1, \dots, y_{n_2})$ est une observation de l'échantillon $(Y_1, \dots, Y_{n_2})$ de loi mère $\mathcal{N}(m_2, \sigma_2^2)$.

# Algorithme

La procédure se déroule de la façon suivante :

1. on teste l'égalité des variances, à l'aide du [[Test de Fisher d'égalité de variances|test de Fisher]] ;
2. et si l'[[Hypothèse nulle et hypothèse alternative|hypothèse]] $\sigma_1^2 = \sigma_2^2$ est acceptée, on teste l'égalité des espérances, à l'aide du [[Test de Student d'égalité de deux moyennes|test de Student]].

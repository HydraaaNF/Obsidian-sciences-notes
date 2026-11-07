#ml-1

# Définition

La [[Précision et rappel|précision]], le rappel et le [[F-mesure F1|F1]] sont définis **par classe**. Pour résumer un classifieur à $N_{cl}$ classes en un seul nombre, deux agrégations s'offrent.

La **moyenne macro** fait la moyenne des scores calculés classe par classe :

$$
F_1^{macro} = \frac{1}{N_{cl}} \sum_{C_i} F_1(C_i)
$$

La **moyenne micro** rassemble d'abord les comptes de toutes les classes, puis calcule le score une seule fois. En notant $TP_i$, $FP_i$ et $FN_i$ les vrais positifs, faux positifs et faux négatifs de la classe $C_i$, et avec

$$
F_1 = \frac{2\,TP}{2\,TP + FP + FN}
$$

on obtient :

$$
F_1^{micro} = F_1\left(\sum_i TP_i, \sum_i FP_i, \sum_i FN_i\right)
$$

# Interprétation

- Moyenne macro : chaque **classe** pèse le même poids.
- Moyenne micro : chaque **échantillon** pèse le même poids.

Le choix de l'agrégation est donc un choix sur ce que l'on veut faire compter. La moyenne macro traite les classes à égalité, y compris les classes rares ; la moyenne micro est dominée par les classes qui fournissent le plus d'échantillons.

# Remarque

Une classe rare peut faire chuter la moyenne macro : son score, même très mauvais, compte autant que celui d'une classe majoritaire bien reconnue.

En classification mono-étiquette, la moyenne micro coïncide avec l'exactitude de la [[Matrice de confusion et exactitude]]. Chaque erreur y produit à la fois un faux positif et un faux négatif, d'où, pour $N$ échantillons, $\sum_i FP_i = \sum_i FN_i = N - \sum_i TP_i$, et

$$
F_1^{micro} = \frac{2\,TP}{2\,TP + 2(N - TP)} = \frac{TP}{N}
$$

qui est bien le taux de bonne classification.

Les deux moyennes divergent nettement : toujours préciser laquelle a été utilisée, par exemple dans un [[Évaluer un classifieur avec scikit-learn|rapport de classification]].

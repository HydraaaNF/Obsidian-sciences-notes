#ml-1

# Définition

La **métrique** est la quantité que l'on veut réellement mesurer ; elle est choisie en fonction de l'application visée.
Elle peut être non différentiable, voire non calculable pendant l'entraînement.

La **perte** $\mathcal{L}$ est une [[Fonction de perte|fonction de perte]] : c'est la quantité que l'algorithme d'entraînement minimise.
Elle est calculée sur un seul échantillon, puis moyennée.
Elle doit être différentiable, puisque l'entraînement suit sa pente.
Elle est choisie comme substitut de la métrique.

# Exemple

Dans une application médicale, une métrique pertinente peut être le nombre de patients manqués : « combien de patients avons-nous manqués ? ».

Pour la régression, les métriques d'erreur usuelles sont présentées dans [[Mesures d'erreur en régression]].

# Remarque

Métrique et perte sont souvent proches, parfois non.
L'exactitude est une métrique, jamais une perte : son gradient est plat.
L'entropie croisée est le substitut de l'exactitude utilisé comme perte, voir [[Entropie croisée binaire]].

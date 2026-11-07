#ml-1

# Définition

La **matrice de confusion** $M$ d'un classifieur compare la classe réelle et la classe prédite : $M[i,j]$ est le nombre d'échantillons de classe $i$ prédits dans la classe $j$.

L'**exactitude** (taux de bonne classification) est la proportion d'échantillons bien classés, c'est-à-dire la masse de la diagonale :

$$
T = \frac{\sum_i M[i,i]}{\sum_{i,j} M[i,j]}
$$

Le **taux d'erreur** en est le complément :

$$
E = 1 - T
$$

# Exemple

Pour trois classes $A$, $B$ et $C$ :

| réel \ prédit | $A$ | $B$ | $C$ |
| --- | --- | --- | --- |
| $A$ | 4 | 2 | 1 |
| $B$ | 4 | 6 | 1 |
| $C$ | 7 | 0 | 9 |

La diagonale totalise $4 + 6 + 9 = 19$ échantillons sur $34$, d'où $T = 19/34 = 56\,\%$ et $E = 44\,\%$.

# Interprétation

Le taux ne dit que la quantité d'erreurs ; la matrice dit **où** le modèle se trompe. Dans la table ci-dessus, $7$ échantillons de classe $C$ sont prédits $A$ : cette information disparaît complètement du seul taux d'exactitude.

La lecture classe par classe, avec les faux positifs et les faux négatifs de chacune, mène à la [[Précision et rappel]] ; ces comptes par classe se lisent directement dans un [[Évaluer un classifieur avec scikit-learn|rapport de classification]].

# Remarque

L'exactitude seule est un piège quand les classes sont déséquilibrées.

- Détection de fraude : $99\,\%$ des transactions sont légitimes, $1\,\%$ sont des fraudes.
- Un modèle qui répond toujours « légitime » atteint $99\,\%$ d'exactitude.
- Il attrape exactement $0$ fraude.

Deux réflexes s'imposent alors :

- toujours comparer le score à celui de la **classe majoritaire**, qui sert de référence minimale ;
- regarder les classes **séparément**, plutôt qu'un unique taux global.

En classification multi-étiquette, l'exactitude trompe dans les deux sens :

- exigée sur toutes les étiquettes à la fois, elle est trop sévère : une seule étiquette manquée sur dix et la photo est comptée fausse ;
- comptée étiquette par étiquette, elle est trop facile : la plupart des étiquettes sont absentes, et l'exemple de la fraude revient.

Examiner les classes séparément suppose de fixer un [[Seuil de décision]] pour décider qu'un échantillon appartient à une classe donnée ; ce seuil déplace les faux positifs et les faux négatifs, donc les scores par classe.

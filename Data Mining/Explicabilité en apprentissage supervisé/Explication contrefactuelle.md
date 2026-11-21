#dmv-xai

# Définition

Une **explication contrefactuelle** répond à la question « what do I need to change in the input to change the model's output? » : elle fournit une instance contrefactuelle, obtenue à partir d'une instance d'origine par la modification d'une partie de ses variables, dont la prédiction par le modèle est différente.

L'instance d'origine est le **factuel** : c'est le cas effectivement observé, avec la prédiction que le modèle lui associe. Le **contrefactuel** est la version modifiée de ce cas, qui franchit la frontière de décision, et se lit toujours par comparaison avec le factuel, variable par variable.

# Propriétés

Un contrefactuel est jugé sur deux qualités qui se compensent.

- la **proximité** : la modification reste aussi proche que possible de l'instance d'origine, en nombre de variables changées comme en amplitude du changement.
- la **plausibilité** : l'instance contrefactuelle reste vraisemblable au regard des données observées, et non un point isolé que le modèle n'aurait jamais rencontré.

Selon l'usage qui en est fait, le contrefactuel prend deux formes.

- **actionnable** : la modification ne porte que sur des variables que la personne concernée peut effectivement changer, ce qui en fait un recours applicable.
- **textuelle** : sur des données de texte, la modification porte sur des mots du document, et le contrefactuel se lit comme une réécriture de celui-ci.

# Exemple

## Chiffres manuscrits

Sur des chiffres manuscrits du jeu de données MNIST, un réseau convolutif prédit la classe de chaque image, et le contrefactuel est une autre image que le réseau classe autrement.

| Image d'origine | Contrefactuel |
| --- | --- |
| 6 | 5 |
| 7 | 9 |
| 8 | 3 |
| 9 | 4 |

## Recensement

Sur une instance du jeu de données Adult (recensement), un réseau de neurones voit sa prédiction de revenu passer de « ≤ \$50k/y » à « > \$50k/y » par le changement de deux variables seulement, les dix autres restant identiques.

| Variable | Origine | Contrefactuel |
| --- | --- | --- |
| Workclass | Private | State-gov |
| Education | High school | Bachelors |
| Marital Status | Married | Married |
| Occupation | Blue-Collar | Blue-Collar |
| Relationship | Husband | Husband |
| Race | White | White |
| Sex | Male | Male |
| Country | United-States | United-States |
| Age | 46 | 46 |
| Capital Gain | 0 | 0 |
| Capital Loss | 0 | 0 |
| Hours p/w | 40 | 40 |
| Prediction | ≤ \$50k/y | > \$50k/y |

## Issue clinique

Sur un cas clinique, seule la tension artérielle distingue le factuel du contrefactuel : les autres variables sont inchangées, et l'issue passe de l'échec au remède.

| Variable | Factuel | Contrefactuel |
| --- | ---: | ---: |
| Age | 25 | 25 |
| Tension | 170 | 190 |
| Sex | Male | Male |
| Weight | 55 | 55 |
| Outcome | ❌ | 💊 |

# Interprétation

L'explication par attribution et l'explication contrefactuelle portent sur deux objets différents.

- L'explication par **attribution** garde l'instance fixe et répartit la prédiction entre les variables, chaque variable recevant une contribution signée qui s'ajoute à une valeur de base.
- L'explication **contrefactuelle** garde la prédiction visée et déplace l'instance, en indiquant quelles variables changer et dans quel sens pour que la prédiction bascule.

La première répond à la question du poids des variables dans la décision prise, la seconde à celle du chemin à parcourir pour en obtenir une autre. La lecture est donc complémentaire : l'attribution explique la prédiction courante, le contrefactuel décrit une prédiction alternative atteignable.

Les deux familles relèvent des explications locales, calculées pour une instance donnée : voir [[Explication locale]], [[SHAP]] et [[Méthodes d'attribution par gradients]] pour l'attribution, [[Algorithmes de génération de contrefactuels]] et [[Contrefactuels pour le texte]] pour le contrefactuel. Un contrefactuel peut aussi être produit par construction, sans recherche a posteriori, avec un réseau entraîné à le générer : voir [[Réseaux de neurones contrefactuels]] et [[Apprentissage de contrefactuels]]. La même construction étendue à un groupe d'instances donne les [[Contrefactuels globaux]], qui relèvent de l'[[Explication globale]].

# Remarque

Le contrefactuel ne décrit pas le mécanisme interne du modèle : il énonce une modification d'entrée dont l'effet sur la sortie est constaté, sans prétendre que cette modification est la cause de la prédiction d'origine.

#ml-1

# Interprétation

Évaluer un [[Modèle d'apprentissage|modèle]] répond à deux questions distinctes :

- ce modèle est-il assez bon ? Il s'agit alors de rendre compte d'une qualité, de comparer deux modèles ou de décider de le mettre en service ;
- dans quelle direction l'améliorer ? Il s'agit alors de conduire l'entraînement lui-même.

Ces deux questions exigent un moyen de mesurer une erreur, fourni par la [[Métrique et fonction de perte|métrique ou la fonction de perte]] choisie.

L'évaluation dépend de la tâche :

- elle ne dépend pas du modèle (linéaire, réseau de neurones, ...) ;
- elle ne dépend pas de la méthode d'optimisation ;
- les mêmes métriques valent donc pour l'ensemble des modèles, quel que soit leur type.

# Remarque

- Comparer deux modèles relève de la [[Sélection de modèle et estimation de la performance|sélection de modèle et de l'estimation de la performance]].
- La mesure de l'erreur suppose de choisir sur quelles données elle est calculée : voir [[Jeux d'entraînement, de développement et de test]].

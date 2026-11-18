#dmv-xai

# Définition

Une **importance de variable par agrégation** est une explication globale obtenue en combinant les explications locales de nombreuses instances : la contribution d'une variable, observée instance par instance, est résumée en un score unique, et la comparaison de ces scores donne le poids relatif de chaque variable dans les prédictions du modèle.

# Propriétés

Deux voies mènent à un score d'importance globale.

- l'agrégation d'explications locales : chaque instance reçoit son explication, puis les contributions d'une même variable sont réunies sur l'ensemble des instances disponibles
- les scores portés par un ensemble d'arbres, fondés sur la baisse d'impureté (*impurity decrease*) ou la chute de précision (*accuracy drop*)

La première voie part de l'[[Explication locale]] et la résume ; la seconde lit l'importance dans le modèle d'arbres lui-même, sans passer par une explication instance par instance. Les deux produisent un score par variable, mais ne l'obtiennent pas au même endroit.

# Exemple

Le jeu de données jouet $W$ range les instances en lignes et les variables en colonnes.

| Élément de la figure | Rôle |
| --- | --- |
| lignes | instances, ici des documents |
| colonnes f1 à f5 | variables, ici des mots |
| colonne f2, en bleu pointillé | variable de plus forte importance |
| lignes 2 et 5, en rouge | instances retenues par la procédure de sélection, couvrant toutes les variables sauf f1 |

Les deux instances retenues couvrent donc f2, f3, f4 et f5, et la variable f1 reste hors de la couverture. Le classement place f2 en tête : sa contribution agrégée domine celle des autres variables.

# Interprétation

Un score d'importance agrégé se lit comme un **classement** : il dit quelles variables pèsent le plus sur les prédictions, et laisse à d'autres résumés le soin de dire comment elles agissent. Une [[Graphique de dépendance partielle|courbe de dépendance partielle]] répond à cette seconde question en traçant la réponse moyenne du modèle pour chaque valeur d'une variable, tandis que l'importance agrégée ne retient qu'un chiffre par variable.

Cette construction est courante pour les explications en attribution de caractéristiques, celles qui répartissent une prédiction entre les variables d'entrée. Elle sert directement les modèles d'ensemble, dont la décision se disperse dans de nombreux arbres : voir les [[Méthodes d'ensemble et machines à vecteurs de support]]. Elle s'inscrit dans la famille des explications globales décrites avec l'[[Explication globale]].

Le score se calcule aussi sur les coefficients d'un modèle dont la lecture est directe, voir le [[Modèle linéaire]] ; les attributions de [[SHAP]], fondées sur la [[Valeur de Shapley]], en fournissent une version par instance, ensuite agrégée.

#dmv-pattern_mining_vs_deep_learning

# Définition

La capture de motifs est l'objectif général de l'analyse des données : extraire d'un jeu de données les régularités qu'il contient.

Le champ des motifs ne se limite pas aux itemsets ni aux séquences : il couvre d'autres formes de régularité, y compris celles des données structurées ([[Extension de la fouille de motifs aux données structurées]]) et des graphes ([[Fouille de motifs de graphes]]).

# Interprétation

Toute méthode d'apprentissage automatique capture une forme de motifs dans les données, que cette capture soit explicite ou non.

La raison est que l'on ne peut ni classer, ni prédire, ni regrouper des données sans aucune structure : une méthode qui y parvient exploite nécessairement des régularités présentes dans les données, donc des motifs.

La capture de motifs n'est ainsi pas propre à la fouille de motifs : elle est le point commun entre fouille de motifs et apprentissage automatique, d'où la question de faire porter l'apprentissage sur des motifs explicites ([[Fouille de motifs et réseaux de neurones profonds]]).

La forme explicite que prend cette capture du côté de la fouille de motifs est le problème de l'ensemble de motifs : trouver un petit ensemble de motifs qui capture les structures principales existant dans les données ([[Ensemble de motifs]]).

# Remarque

Les motifs trouvés par une méthode d'apprentissage automatique sont un sous-produit de cette méthode :

- ils ne sont pas conçus pour être compris par un humain ;
- il est souvent difficile de les retrouver dans le modèle une fois celui-ci entraîné ;
- ils contiennent néanmoins une information précieuse sur les données.

La difficulté est donc celle de l'accès au motif, non celle de son contenu : le motif est bien présent dans le modèle, mais malaisé à en extraire.


#ml-1

# Interprétation

L'évaluation d'un [[Clustering|clustering]] dépend de la disponibilité d'étiquettes sur le jeu de test.

Si le jeu de test est étiqueté, le clustering s'évalue comme un classifieur : les clusters sont d'abord appariés aux classes, puis les métriques de classification s'appliquent à cet appariement.

Sans étiquettes, trois voies restent disponibles :

- les critères internes, qui récompensent des clusters compacts et bien séparés, à l'aide des [[Mesures de similarité et de distance|distances entre points]] ; la [[Qualité d'un clustering|qualité d'un clustering]] détaille ces critères ;
- l'évaluation humaine, qui cherche si les clusters ont un sens ;
- l'évaluation applicative, qui vérifie si la tâche en aval s'améliore grâce au clustering.

# Remarque

Un cluster et une classe n'ont aucune raison de porter le même nom : le cluster 3 et la classe « chien » désignent deux découpages distincts, et rien ne garantit qu'ils se correspondent terme à terme.

L'appariement des clusters aux classes est donc indispensable avant de calculer la moindre métrique de classification.

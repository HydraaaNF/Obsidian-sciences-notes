#dmv-pattern_mining_with_information_theory
# Interprétation

Une table de codes n'a d'intérêt que par ce qu'elle permet de faire des données. Sa qualité a donc été éprouvée en la mettant au service de tâches aval variées, chacune exploitant le fait que la table résume la structure locale des transactions.

Les applications testées couvrent :

- la classification,
- la mesure de dissimilarité entre transactions,
- la génération de données,
- la détection de dérive de concept,
- l'estimation de valeurs manquantes,
- le clustering,
- le clustering en sous-espaces,
- la détection d'anomalies,
- la caractérisation de données 0-1 incertaines,
- la recommandation de tags,
- le Web sémantique.

# Remarque

Ces applications illustrent trois usages du modèle, sans épuiser la liste :

- **décider** : la table sert de modèle de classe, comme en [[Classification par compression avec des tables de codes|classification par compression]], où la classe retenue est celle dont la table encode le plus court ;
- **comparer** : la table fournit une base de mesure de dissimilarité ;
- **compléter ou caractériser** : la table sert de modèle des régularités pour estimer une valeur manquante, signaler une transaction atypique ou décrire des données incertaines.

Cette lecture ne prétend pas couvrir toute la liste : la génération de données, la détection de dérive de concept, le clustering, le clustering en sous-espaces, la recommandation de tags et le Web sémantique restent hors de ces trois usages.

Le point commun est que la table de codes remplace un ensemble de motifs à examiner par un modèle directement utilisable : sa taille réduite et sa spécificité, décrites dans les [[Propriétés des tables de codes de KRIMP]], sont ce qui rend ces traitements praticables.

Une table de codes n'est jamais appliquée seule : elle est apprise sur une base, puis sert à encoder des transactions, ce qui suppose de savoir mesurer la [[Longueur de description d'une base encodée|longueur de description d'une transaction encodée]].

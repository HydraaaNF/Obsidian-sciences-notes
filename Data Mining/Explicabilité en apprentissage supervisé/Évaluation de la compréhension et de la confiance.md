#dmv-xai

# Définition

L'évaluation centrée utilisateur d'une explication porte sur la personne qui la reçoit, et non sur l'explication ni sur la méthode qui la produit : elle mesure la compréhension que l'utilisateur en retire et la confiance qu'il accorde au modèle. Elle complète les [[Critères et métriques d'évaluation d'une explication|critères fonctionnels]].

# Interprétation

Aucune des deux grandeurs ne s'observe directement.

La compréhension s'évalue le plus souvent au moyen d'une tâche proxy, c'est-à-dire d'une tâche dont la réussite tient lieu de preuve de compréhension.

- prédire la réponse du modèle pour une instance donnée
- expliquer les caractéristiques qui jouent un rôle dans la prédiction
- valider ou rejeter des affirmations sur le modèle
- remplacer le modèle, épreuve également employée pour mesurer la confiance

La confiance s'évalue par des questionnaires et par l'adhérence à la recommandation du système d'intelligence artificielle, c'est-à-dire par la confiance que l'utilisateur lui accorde.

La tâche proxy fournit un comportement mesurable, auquel s'ajoutent des métriques comportementales et auto-déclarées.

- la précision ou l'exactitude des réponses à la tâche proxy
- le temps d'exécution de la tâche, c'est-à-dire le temps de décision demandé à l'utilisateur
- des questionnaires spécialisés, qui recueillent un jugement que le comportement seul ne montre pas

La confiance est un construit complexe.

- un questionnaire ne teste pas la confiance elle-même, mais un construit qui lui est apparenté
- ses réponses ne sont donc que des proxys de la confiance, et non une mesure directe

Ces mesures se combinent dans un dispositif complet de comparaison, décrit par le [[Protocole de comparaison d'explications]].

# Exemple

Le questionnaire de confiance se compose de quatre questions, notées de 1 à 6 ; seules les deux extrémités de l'échelle portent un libellé.

| N° | Question | 1 | 2 | 3 | 4 | 5 | 6 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Quelle est votre confiance dans l'outil ? Éprouvez-vous un sentiment de confiance à son égard ? | Je ne lui fais pas du tout confiance. | 2 | 3 | 4 | 5 | Je lui fais entièrement confiance. |
| 2 | Les actions de l'outil sont-elles prévisibles ? | Elles ne sont pas du tout prévisibles. | 2 | 3 | 4 | 5 | Elles sont entièrement prévisibles. |
| 3 | L'outil est-il fiable ? | Il n'est pas du tout fiable. | 2 | 3 | 4 | 5 | Il est entièrement fiable. |
| 4 | L'outil est-il efficace dans ce qu'il fait ? | Il n'est pas du tout efficace. | 2 | 3 | 4 | 5 | Il est entièrement efficace. |

Chaque question isole une facette distincte de la confiance : le sentiment de confiance, la prévisibilité des actions, la fiabilité et l'efficacité.

# Remarque

La confiance recouvre trois phénomènes distincts : la confiance, la défiance et la complaisance, c'est-à-dire la sur-confiance. La [[Critères et métriques d'évaluation d'une explication|grille des critères centrés utilisateur]] les range sous le même critère.

L'excès de confiance correspond au biais d'automatisation : la tendance à s'appuyer automatiquement sur la sortie d'un système d'intelligence artificielle à haut risque, voire à s'y fier excessivement, en particulier lorsque ce système sert à fournir des informations ou des recommandations pour une décision prise par une personne.

Un score élevé au questionnaire ne suffit donc pas à conclure à une bonne explication : la compréhension se mesure à part, par une tâche proxy.

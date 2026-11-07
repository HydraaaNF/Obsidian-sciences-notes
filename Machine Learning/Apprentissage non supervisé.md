#ml-1

# Définition

L'**apprentissage non supervisé** est le cadre d'apprentissage où les données disponibles sont uniquement **non étiquetées** : les classes que l'on cherche à faire apparaître sont inconnues, tant en nombre qu'en nature.

Le modèle apprend alors une fonction $f(x) = y$ dont la sortie $y$ n'est fournie par aucune donnée : la valeur à prédire reste inconnue. L'objectif n'est pas d'imiter des étiquettes, mais de faire émerger une structure dans les observations.

# Exemple

La catégorisation d'oiseaux :

- en entrée, la taille, la couleur, l'alimentation et d'autres attributs d'un individu ;
- en sortie recherchée, une catégorisation des individus en groupes, sans connaître à l'avance ni le nombre ni la nature de ces groupes.

Rechercher le thème d'un texte ou le genre d'une chanson relève de la même démarche : la sortie attendue n'est pas donnée avec les données.

Un nuage de points non étiquetés illustre le principe : les observations forment une région, et l'apprentissage en tire une fonction $f(x) = y$ dont la valeur de $y$ demeure inconnue.

# Remarque

Le [[Clustering|clustering]] est la tâche non supervisée de partitionnement : il regroupe les observations en classes dont le nombre et la nature ne sont pas fixés au départ. On le décrit aussi comme une **classification non supervisée**, par symétrie avec la classification étiquetée. Les [[Types de clustering]] distinguent les familles de méthodes, et l'[[Évaluation d'un clustering]] mesure la qualité des groupes obtenus.

L'apprentissage non supervisé s'oppose à l'[[Apprentissage supervisé]], où chaque exemple est accompagné de la valeur à prédire. Il correspond au cas non étiqueté des [[Régression, classification et clustering|trois familles de tâches]].

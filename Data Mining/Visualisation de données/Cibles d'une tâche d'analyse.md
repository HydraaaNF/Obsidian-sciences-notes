#dmv-visualization

# Définition

La cible d'une tâche d'analyse est ce que l'utilisateur cherche dans les données. Elle se classe selon le type de données concerné.

| Type de données | Cibles |
| :--- | :--- |
| Toutes données | tendances, valeurs aberrantes, caractéristiques |
| Données de réseau | topologie, chemins |
| Un attribut | distribution, valeurs extrêmes |
| Plusieurs attributs | dépendance, corrélation, similarité |
| Données spatiales | forme |

Chaque cible se combine avec une action de recherche : on cherche une tendance, une topologie ou une distribution en identifiant, comparant ou résumant, requêtes décrites dans [[Recherche et requête dans une visualisation]].

# Interprétation

La cible dépend d'abord du [[Types de jeux de données]] : une table autorise la recherche de tendances et de valeurs aberrantes sur ses attributs, un réseau celle de sa topologie et de ses chemins, un champ spatial celle de sa forme.

Le niveau d'abstraction compte autant que le type : chercher la distribution d'un seul attribut n'est pas chercher la dépendance entre plusieurs attributs, et une corrélation entre attributs n'est pas une similarité entre attributs.

# Remarque

L'abstraction des tâches combine deux axes : l'action, qui dit comment chercher, décrite par les [[Actions d'une tâche d'analyse]], et la cible, qui dit quoi chercher. Les deux se décrivent ensemble dans l'[[Abstraction des tâches d'analyse]], et la cible contraint le choix de la représentation autant que l'action.

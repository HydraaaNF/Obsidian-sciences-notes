#dmv-visualization

# Modèle

Les actions de recherche d'information se classent selon deux questions : la cible recherchée est-elle connue, et sa localisation est-elle connue.

| | Cible connue | Cible inconnue |
| :--- | :---: | :---: |
| **Localisation connue** | Lookup | Browse |
| **Localisation inconnue** | Locate | Explore |

La famille Query regroupe trois tâches :

- Identify : identifier une cible précise ;
- Compare : comparer plusieurs cibles ;
- Summarize : résumer l'ensemble des cibles.

# Interprétation

Les quatre cases de la recherche décrivent ce que l'utilisateur sait déjà :

- cible et localisation connues : lookup, la cible est retrouvée à un endroit connu ;
- cible connue, localisation inconnue : locate, il faut trouver où se trouve la cible ;
- localisation connue, cible inconnue : browse, le parcours se fait à l'intérieur d'une zone connue ;
- ni cible ni localisation connues : explore, la tâche la plus ouverte.

# Remarque

Recherche et requête sont deux familles d'[[Actions d'une tâche d'analyse|actions d'une tâche d'analyse]] ; les objets sur lesquels elles portent, tendances, valeurs aberrantes, topologie ou distribution, sont décrits dans [[Cibles d'une tâche d'analyse]].

Le résultat d'une recherche ou d'une requête est ensuite exploité par modification de la vue, décrite dans [[Manipulation d'une visualisation]].

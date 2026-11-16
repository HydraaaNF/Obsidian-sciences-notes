#dmv-subgroup_discovery

# Définition

La tâche de découverte de sous-groupes consiste à trouver des **descriptions** de sous-ensembles des données qui diffèrent significativement de la population totale vis-à-vis d'un **concept cible**.

Une description sélectionne un sous-ensemble d'individus et prend la forme d'un [[Motif de sous-groupe|motif de sous-groupe]] ; le concept cible est porté par les attributs cibles, dont la distribution dans le sous-ensemble est comparée à celle de la population totale (voir [[Attributs de description et attributs cibles]]). L'ampleur de l'écart se mesure par une [[Fonction de qualité d'un sous-groupe|fonction de qualité]].

# Exemple

Parmi les étudiants d'une université, 80 % des étudiants de Computer Science sont des hommes, contre 50 % sur l'ensemble des étudiants de l'université.

```chart
type: bar
labels: ["Computer Science", "Tous les étudiants"]
series:
  - title: Proportion d'hommes (%)
    data: [80, 50]
```

Le sous-ensemble décrit par le cursus suivi s'écarte nettement de la population totale : la proportion d'hommes y passe de 50 % à 80 %.

# Remarque

Le caractère significatif de l'écart se juge avec la [[Fonction de qualité d'un sous-groupe|fonction de qualité]] : c'est elle qui décide si la différence observée suffit à retenir le sous-groupe. Le cadre général de la démarche est décrit dans [[Principe de la découverte de sous-groupes]].

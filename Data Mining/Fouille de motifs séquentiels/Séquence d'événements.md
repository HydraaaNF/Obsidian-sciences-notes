#dmv-sequence_mining

# Définition

Une séquence d'événements décrit une activité observée au cours du temps : chaque événement y est daté.

Un **événement** est un couple $(E,t)$ où $E$ est un type d'événement et $t$ son instant d'occurrence.

Les types d'événements disponibles forment un ensemble fini $R$, par exemple

$$R = \{\text{A = 'eat'}, \text{B = 'work'}, \text{C = 'prepare coffee'}, \text{D = 'wake up'}\}.$$

Les instants d'occurrence sont des entiers, ici compris entre 10 et 150.

Une **séquence** sur $R$ est un triplet $S = (s, T_s, T_e)$ où :

- $s$ est la suite des événements ordonnés dans le temps, $s = \langle (D,10), (C,20), \dots, (A,150) \rangle$ ;
- $T_s$ est l'instant de début de l'observation, $T_s = 10$ ;
- $T_e$ est l'instant de fin de l'observation, $T_e = 150$.

Un créneau temporel peut contenir 0, 1 ou plusieurs événements.

# Exemple

Trace d'activité humaine sur l'intervalle $[0, 150]$ :

| $t$ | 0 | 10 | 20 | 30 | 40 | 50 | 60 | 70 | 80 | 90 | 100 | 110 | 120 | 130 | 140 | 150 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Événement** | | D | C | A | B | D | A | B | C | A | D | C | A | B | D | A |

Avec les types $R$ ci-dessus, l'événement survenu à l'instant 30 est $(A, 30)$, c'est-à-dire une prise de repas.

La séquence correspondante commence à $T_s = 10$ et se termine à $T_e = 150$ ; le créneau d'instant 0 ne porte aucun événement.

# Remarque

La même trace sert de support aux notions dérivées de la fouille d'épisodes, selon deux approches. L'[[Algorithme WINEPI]] fait glisser une [[Fenêtre glissante de WINEPI|fenêtre glissante]] le long de la séquence et observe les [[Épisode|épisodes]] dans chaque fenêtre. L'[[Algorithme MINEPI]] ne découpe pas de fenêtres : pour chaque épisode candidat, il recherche ses occurrences minimales exactes.

Une séquence d'événements est le cadre d'entrée de la [[Fouille d'épisodes dans une séquence d'événements]], à distinguer de la [[Base de séquences]] utilisée pour les [[Motif séquentiel|motifs séquentiels]] : ici les événements sont datés et l'ordre des types successifs n'est qu'une des relations possibles entre eux.

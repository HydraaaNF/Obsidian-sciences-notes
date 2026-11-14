#dmv-visualization

# Interprétation

Dans une analyse pilotée par l'utilisateur, la question n'est pas connue à l'avance : elle émerge du processus d'analyse lui-même, au fil des vues examinées.

Le processus est conduit par l'utilisateur, qui décide à chaque étape de ce qu'il regarde ensuite et de la suite à donner à l'analyse.

La démarche exploite la capacité des humains à trouver des motifs : un alignement, une rupture de pente ou un groupe isolé se repèrent à l'œil sans avoir été cherchés explicitement.

Elle augmente ainsi le processus de décision humain et vise l'amélioration de la prise de décision, là où une chaîne entièrement automatique se substituerait au jugement : c'est le versant humain de la [[Complémentarité de la visualisation et des méthodes automatiques|complémentarité entre visualisation et méthodes automatiques]].

Ce mode d'exploration rejoint l'[[Interactivité de la visualisation|interactivité de la visualisation]] : chaque geste de l'utilisateur reformule la question posée aux données. Voir [[Faire entrer l'ordinateur dans la boucle d'analyse]].

# Exemple

Une série d'intervalles RR, c'est-à-dire des durées séparant deux battements cardiaques successifs, est tracée en fonction du temps pour un échantillon unique d'environ neuf minutes :

- l'ordonnée porte l'intervalle RR en secondes, de 0,6 à 1,2 s
- l'abscisse porte le temps, de 00:00:00 à 00:09:00, graduée de 50 s en 50 s jusqu'à 00:08:20
- la détendanciation se fait par lissage à a priori de type smoothn, avec $\lambda = 300$
- la vue ne pose aucune question fermée, ce que traduit le point d'interrogation qui l'accompagne : c'est à l'utilisateur de repérer les motifs de la série

Les bornes des axes et la valeur du paramètre de lissage sont relevées sur la figure.

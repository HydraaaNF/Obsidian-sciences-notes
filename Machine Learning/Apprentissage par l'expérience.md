#ml-1

# Définition

L'apprentissage par l'expérience consiste à **généraliser à des situations inconnues** : à partir de cas déjà rencontrés, produire une réponse correcte sur des cas nouveaux, c'est-à-dire savoir faire plus que ce qui a été appris au sens strict.

# Exemple

Conditionnement de Pavlov. Un chien est exposé à deux stimuli, un os et une cloche, et l'on observe sa réponse à chacun.

| Phase | Stimulus | Réponse |
| :--- | :--- | :--- |
| Avant le conditionnement | Os | Salivation |
| Avant le conditionnement | Cloche | Aucune réponse |
| Pendant le conditionnement | Cloche et os | Salivation |
| Après le conditionnement | Cloche | Salivation |

La cloche, d'abord neutre, finit par déclencher seule la salivation : l'animal a acquis une association par l'expérience, et cette association se conserve en l'absence de l'os.

# Exemple

Face à la suite $1, 2, 3, 5, a$, une question naturelle est : que devrait valoir $a$, ou que pourrait-il valoir ? Plusieurs lois rendent compte des quatre premiers termes :

- $a = 6$, avec la règle « tous les entiers sauf 4 » ;
- $a = 7$, avec la règle « les nombres premiers » ;
- $a = 8$, avec la règle de Fibonacci.

D'autres règles restent possibles. Les observations sont les mêmes et ne désignent aucune de ces lois à elles seules : expliquer une loi cachée à partir d'exemples demande un critère de choix, fourni par le [[Rasoir d'Occam|rasoir d'Occam]], qui retient l'explication construite avec le plus petit ensemble d'éléments.

# Exemple

Apprendre à conduire : les leçons se prennent sur une Renault Clio, puis on passe son permis ; une fois chez soi, on conduit la Hummer de son père ou la Ferrari de sa mère. La compétence acquise sur une petite voiture se transfère à des véhicules très différents, et l'on sait alors faire plus que ce qui a été appris au sens strict.

# Remarque

La généralisation est ce que montrent les exemples de cette note : la salivation déclenchée par la cloche seule, et la conduite d'un véhicule jamais conduit.

Les situations inconnues visées relèvent des [[Problèmes d'apprentissage statistique|problèmes d'apprentissage statistique]], dont les tâches usuelles sont la [[Régression, classification et clustering|régression et la classification]].

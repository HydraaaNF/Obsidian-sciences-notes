# Définition

Le [[Clustering hiérarchique|clustering hiérarchique]] peut être construit de deux façons :

- **Agglomératif** (ascendant, bottom-up) : construction ascendante du dendrogramme par fusion progressive des clusters. Chaque point est initialement un cluster ; on combine répétitivement les deux clusters « les plus proches » en un seul.
- **Divisif** (descendant, top-down) : construction descendante du dendrogramme. On part d'un unique cluster et on le scinde récursivement ; l'algorithme associé est DIANA (Divisive ANAlysis).

# Algorithme

Déroulement de la construction agglomérative :

```
initialiser N clusters singletons
nclusters ← N
tant que nclusters > 0 faire
  fusionner les deux clusters les plus proches
  nclusters ← nclusters - 1
fin tant que
```

# Remarque

L'intitulé « divisive bottom-up clustering » est parfois employé pour désigner le clustering divisif ; il est contradictoire, car la construction divisive est descendante (top-down), elle part d'un unique cluster que l'on scinde récursivement, tandis que « bottom-up » qualifie la construction agglomérative, ascendante, qui part de clusters singletons et les fusionne progressivement.

Pour la mise en œuvre de la construction agglomérative, voir [[Matrice de proximité et clustering ascendant]] et [[Types de liaison entre clusters]].

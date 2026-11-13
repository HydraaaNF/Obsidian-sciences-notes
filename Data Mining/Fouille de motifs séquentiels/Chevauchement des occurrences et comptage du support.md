#dmv-sequence_mining

# Remarque

Pour des données ensemblistes, le comptage du support ne pose pas de difficulté : l'inclusion y est l'opération ensembliste simple $\subseteq$, et le [[Support d'un itemset|support d'un itemset]] se lit directement dans la base de transactions.

Sur des données structurées (séquences, arbres, graphes), un motif peut apparaître plusieurs fois dans une même donnée, et les occurrences trouvées peuvent se chevaucher : deux occurrences partagent alors des éléments, sans être identiques ni indépendantes. Le support n'est donc plus déterminé par la seule donnée qui contient le motif.

La question à trancher est celle du comptage du support :

- compter une donnée une seule fois dès qu'elle contient au moins une occurrence du motif ;
- compter chaque occurrence séparément, au risque de compter plusieurs fois la même donnée.

Les deux conventions ne donnent pas le même support. Le choix est indissociable de la définition de l'inclusion retenue, voir [[Identification de motif dans des données structurées]], et il est fixé par la définition du [[Support d'un motif séquentiel|support d'un motif séquentiel]].

# Exemple

Sur une molécule, un même fragment structural apparaît deux fois ; les deux occurrences partagent une partie de leurs atomes et se recouvrent donc partiellement. Une seule molécule porte pourtant les deux occurrences : selon la convention retenue, le fragment y est présent une fois ou deux.

# Interprétation

Le mode de comptage n'est pas un détail d'implémentation : il décide de ce que l'algorithme énumère et de la manière dont il restreint la partie de la donnée encore à explorer. Un parcours par projection, qui conserve les portions de données où les occurrences restantes peuvent se trouver, hérite directement de la convention choisie, voir [[Base projetée]].

#ml-1

# Définition

Une tâche sur des séquences se caractérise par la forme de son entrée et celle de sa sortie : chacune est soit un élément isolé, soit une séquence d'éléments.

| Configuration | Entrée | Sortie |
| --- | --- | --- |
| one to one | un élément | un élément |
| one to many | un élément | une séquence |
| many to one | une séquence | un élément |
| many to many | une séquence | une séquence, de longueur différente de celle de l'entrée et sans alignement position par position |
| many to many | une séquence | une séquence, un élément de sortie par élément d'entrée |

# Exemple

- one to one : une image et sa classe ;
- one to many : une image et sa légende ;
- many to one : un avis et son opinion, ou $W$ mois et le mois suivant ;
- many to many : une phrase et sa traduction ;
- many to many : l'étiquetage, une étiquette par mot.

# Interprétation

Sur les schémas de ces tâches, les entrées sont en rouge, les sorties en bleu, et en vert la mémoire du réseau, transmise d'un pas à l'autre.

Le module de calcul se répète à chaque pas de temps, et c'est la mémoire verte qui transporte l'information d'un pas au suivant : c'est le principe du [[Réseau récurrent]].

La source donne le même nom, many to many, aux deux dernières colonnes : elles ne se distinguent que par leur exemple et par leur schéma. Pour la traduction, la sortie n'a pas la longueur de l'entrée et aucun élément de sortie ne correspond à une position donnée de l'entrée (sur le schéma, trois entrées pour deux sorties) ; pour l'étiquetage, chaque élément de l'entrée reçoit son élément de sortie, ce qui fait qualifier cette variante de synchronisée.

# Remarque

- Un réseau feed-forward ne réalise que la première configuration, one to one.
- Les autres configurations portent sur des [[Données séquentielles]], dont l'ordre des éléments compte et dont la longueur n'est pas fixée à l'avance : voir [[Longueur variable des séquences]].

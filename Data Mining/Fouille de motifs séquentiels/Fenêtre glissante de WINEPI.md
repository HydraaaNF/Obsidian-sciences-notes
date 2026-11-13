#dmv-sequence_mining

# Définition

La fenêtre glissante est la technique sur laquelle repose la méthode WINEPI : une fenêtre de largeur fixe est déplacée le long d'une [[Séquence d'événements]].

Chaque instantané de la fenêtre, c'est-à-dire la suite des événements qu'elle couvre à une position donnée, joue le rôle d'une ligne d'une base de données ; la collection de ces instantanés forme les lignes de cette base.

Deux conventions fixent le découpage :

- le dernier point de la fenêtre est exclu ;
- la première (respectivement la dernière) fenêtre contient le premier (respectivement le dernier) point de la séquence.

# Interprétation

La fenêtre glissante transforme une séquence d'événements unique en une base de séquences, ce qui ramène la [[Fouille d'épisodes dans une séquence d'événements|fouille d'épisodes]] à un comptage : un [[Épisode]] est cherché dans chaque instantané, et sa [[Fréquence d'un épisode|fréquence]] est la proportion d'instantanés qui le contiennent.

C'est ce découpage qui donne son nom à la méthode, mise en œuvre par l'[[Algorithme WINEPI]], et qui l'oppose à l'[[Algorithme MINEPI]], lequel travaille sans fenêtre, directement sur les [[Occurrence minimale d'un épisode|occurrences minimales]] des épisodes.

# Exemple

La séquence d'événements

$$D,\ C,\ A,\ B,\ D,\ A,\ B,\ C$$

découpée par une fenêtre de largeur 40 s, donne onze instantanés :

| N° | Instantané |
| :---: | :--- |
| 1 | D |
| 2 | DC |
| 3 | DCA |
| 4 | DCAB |
| 5 | CABD |
| 6 | ABDA |
| 7 | BDAB |
| 8 | DABC |
| 9 | ABC |
| 10 | BC |
| 11 | C |

La collection de ces instantanés, du premier au onzième, constitue la base sur laquelle porte ensuite le décompte.

# Remarque

Le nombre d'instantanés dépend de la largeur retenue : c'est cette largeur qui fixe le dénominateur de la [[Fréquence d'un épisode]].

Un épisode n'est compté qu'une fois par fenêtre où il se produit, même s'il y apparaît de plusieurs façons ; le décompte porte sur les onze instantanés de l'exemple.

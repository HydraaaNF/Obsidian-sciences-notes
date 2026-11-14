#dmv-visualization

# Définition

Un jeu de données se range dans un type défini par la forme de son organisation, chacun ayant ses composants propres.

| Type de jeu de données | Composants |
| :--- | :--- |
| Table | items (lignes), attributs (colonnes), cellule contenant une valeur |
| Réseau | nœuds (items), liens |
| Champ continu | grille de positions, cellule, attributs (colonnes), valeur dans la cellule |
| Table multidimensionnelle | clé 1, clé 2, attributs, valeur dans la cellule |
| Arbre | nœuds reliés par une relation hiérarchique |
| Géométrie spatiale | positions |

La disponibilité du jeu de données se caractérise aussi :

- *statique* : le jeu de données est fixé ;
- *dynamique* : il évolue, notamment au cours du temps.

Les données manipulées, indépendamment du type de jeu, se répartissent en cinq catégories :

- items ;
- attributs ;
- liens ;
- positions ;
- grilles.

# Exemple

Un jeu de données de cooccurrences de personnages se présente comme une suite de lignes, chacune repérée par une clé numérique hiérarchique et énumérant des paires de personnages qui apparaissent ensemble :

```text
1.1.1:MY,NP;MY,MB
1.1.2:MY,ME;ME,MB
1.1.3:MY
1.1.4:MY,ME;MY,CL;MY,GE;MY,MC;MY,MB
```

Chaque ligne est un item, chaque paire un lien entre deux personnages : le même contenu se lit donc comme une table (items et attributs) ou comme un réseau (nœuds et liens), selon le type de jeu de données retenu pour le représenter.

# Remarque

Le type de jeu de données conditionne la représentation choisie : un réseau appelle une représentation de réseau, une table une représentation tabulaire ou un nuage de points. Le choix du type précède donc le choix des marques et des canaux, et se combine avec celui des [[Attribut et types d'attributs]].

Les champs continus et la géométrie spatiale relèvent de la [[Visualisation scientifique et visualisation d'information|visualisation scientifique]], les réseaux et les tables de haut niveau abstrait de la visualisation d'information ; les seconds se représentent par les techniques de [[Représentation visuelle des réseaux]]. Un champ de tenseurs est un champ continu dont chaque cellule porte un tenseur, ce que traite la [[Visualisation de tenseurs]].

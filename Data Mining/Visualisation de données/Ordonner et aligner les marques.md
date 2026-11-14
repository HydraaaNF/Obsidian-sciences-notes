#dmv-visualization

# Définition

Parmi les procédés qui arrangent les données dans la vue, deux opérations portent sur la position des marques :

- ordonner (*Order*) : ranger les marques le long d'un axe selon une mesure, de sorte que la position encode l'ordre des valeurs ;
- aligner (*Align*) : placer les marques sur une échelle ou un axe commun, de sorte que leurs positions soient comparables d'une marque, d'un groupe ou d'une vue à l'autre.

Ordonner exploite les valeurs pour choisir une séquence ; aligner exploite une échelle partagée pour rendre les écarts lisibles.

# Exemple

La carte de chaleur de groupes (*cluster heatmap*) combine les deux : les lignes et les colonnes sont réordonnées par regroupement, ce qui fait apparaître des blocs de valeurs semblables, et toutes les cellules sont alignées sur une même grille, ce qui rend les intensités comparables d'une ligne à l'autre.

Les [[Coordonnées parallèles]] en donnent une autre variante : chaque attribut occupe un axe vertical, toutes les observations sont alignées sur ces mêmes axes, et l'ordre des axes comme l'ordre des lignes sont des choix d'arrangement.

# Remarque

L'ordre est un arrangement, pas un encodage : il ne crée pas de canal visuel nouveau, il exploite la position existante pour rendre une structure lisible. Il se combine donc avec les autres procédés d'arrangement, la [[Séparer les marques sans recouvrement|séparation des marques sans recouvrement]] en particulier, et sert l'objectif d'[[Exprimer toutes les données dans la vue]].

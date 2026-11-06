# Propriétés

Le [[k-means]] présente les avantages et inconvénients suivants.

**Avantages**

- simple, clair et populaire ;
- raisonnablement efficace ;
- convergence garantie ;
- peut s'adapter à toute forme (avec suffisamment de clusters).

**Inconvénients**

- initialisation et [[Propriétés du k-means|optima locaux]] ;
- nécessité de définir le [[Choix du nombre de clusters|nombre de clusters]] ;
- clusters convexes, de taille et de densité à peu près comparables ;
- tendance à créer des cellules déséquilibrées ;
- très sensible au bruit et aux outliers.

# Interprétation

Le découpage s'organise en cellules autour des centres, chaque point étant affecté au centre dont il est le plus proche ; ces cellules peuvent être de tailles très inégales.

# Exemple

Deux jeux de données en deux dimensions, avec les clusters obtenus et leurs centres marqués d'une croix :

- un groupe de points très étalé voisine avec deux groupes compacts : la partition en trois clusters scinde le groupe étalé en deux et réunit les deux groupes compacts en un seul ;
- une structure en spirale, dont deux bras s'enroulent l'un autour de l'autre : la partition en deux clusters coupe les deux bras au lieu de les séparer.

# Remarque

Voir aussi les avantages et inconvénients du [[Avantages et inconvénients du clustering hiérarchique|clustering hiérarchique]] et ceux de [[Avantages et inconvénients de DBSCAN|DBSCAN]].

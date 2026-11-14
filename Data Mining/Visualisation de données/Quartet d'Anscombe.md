#dmv-visualization

# Définition

Le quartet d'Anscombe est un ensemble de quatre jeux de données, numérotés I à IV, construits pour partager exactement les mêmes statistiques sommaires :

- moyenne de $x$ : $9{,}0$ ;
- variance de $x$ : $10{,}0$ ;
- droite de régression linéaire : $y = 3 + 0{,}5\,x$.

Les quatre jeux sont donc indiscernables dès qu'on ne regarde que ces résumés, alors que leurs structures sont très différentes.

# Exemple

Le nuage de points de chaque jeu, muni de la même droite de régression, montre quatre situations distinctes :

- jeu I : les points suivent effectivement une relation linéaire croissante, avec une dispersion modérée de part et d'autre de la droite ;
- jeu II : la relation est nettement curviligne, en arc de cercle, et la droite de régression la résume mal ;
- jeu III : la relation est linéaire, mais un point aberrant situé en haut à droite tire la droite et fausse le résumé ;
- jeu IV : tous les points sont alignés sur une même abscisse, sauf un point isolé très à droite, qui détermine à lui seul la pente.

La moyenne et la variance de $x$, comme la droite de régression, coïncident, mais aucune des quatre figures ne se ressemble : la structure détaillée du jeu de données en dit plus qu'un résumé statistique.

# Remarque

Le quartet est l'argument en faveur de l'exploration visuelle : il faut regarder les données pour y trouver des motifs, une poignée d'indicateurs numériques pouvant masquer des formes aussi différentes qu'une courbe, un point aberrant ou un point de levier. C'est la raison d'être de la [[Visualisation assistée par ordinateur]].

Les deux vues utiles ici sont complémentaires : le [[Nuage de points pour données multidimensionnelles]] montre la forme de la relation, la [[Lecture d'une boîte à moustaches]] résume une distribution par ses quartiles et ses valeurs extrêmes.

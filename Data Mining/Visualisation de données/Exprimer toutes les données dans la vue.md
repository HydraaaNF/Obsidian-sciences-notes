#dmv-visualization

# Interprétation

Exprimer consiste à faire figurer dans la vue toutes les valeurs du jeu de données : aucune valeur n'est omise, aucune n'est agrégée avant d'être montrée.

L'échelle choisie décide de ce qui reste effectivement visible. Un axe linéaire donne la même longueur à un même écart de valeur : les valeurs d'une distribution très asymétrique s'écrasent près de l'origine et disparaissent. Un axe logarithmique donne la même longueur à un même rapport de valeurs : ce sont alors les valeurs voisines de l'origine qui s'espacent, tandis que les valeurs proches du maximum se tassent contre le bord.

Exprimer n'est donc pas seulement dessiner toutes les marques, c'est choisir un cadre dans lequel chacune d'elles porte encore une position lisible.

# Exemple

Prix de diamants en fonction de leur carat :

- en axes linéaires, la masse des petits diamants s'écrase près de l'origine et seule la pointe des plus gros reste lisible
- en axes logarithmiques sur les deux dimensions, les petits diamants s'étalent, les gros se resserrent vers la droite, et la relation croissante entre carat et prix s'aligne sur une droite

Le nuage de points de [[Nuage de points pour données multidimensionnelles|The Wealth & Health of Nations]] exprime de la même façon plusieurs attributs à la fois :

- un cercle par pays
- la position porte le revenu par habitant en abscisse et l'espérance de vie en ordonnée
- la taille et la couleur portent deux attributs supplémentaires
- l'année est affichée en clair et l'animation la fait défiler

# Remarque

Exprimer est le premier des arrangements de la famille des questions du comment, aux côtés de la [[Séparer les marques sans recouvrement|séparation]], de l'ordonnancement et de l'alignement : voir [[Questions du comment en conception de visualisation]]. Quand le volume interdit de tout montrer, c'est la [[Réduction des données affichées]] qui prend le relais.

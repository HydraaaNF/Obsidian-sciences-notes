#dmv-visualization

# Définition

Le diagramme en ensembles parallèles représente un jeu de données catégorielles par une suite d'axes verticaux, un par variable. Sur chaque axe, les catégories sont empilées en bandes dont la hauteur est proportionnelle à l'effectif, et des rubans relient les bandes d'un axe à l'axe suivant : la largeur d'un ruban est proportionnelle au nombre d'observations qu'il transporte.

Le diagramme se lit donc comme un tableau de contingence rendu par des épaisseurs : suivre un ruban d'un bord à l'autre décrit une combinaison de catégories, et sa largeur en donne l'effectif.

# Exemple

Le jeu de données des survivants du *Titanic* se lit sur quatre axes : survie (péri, survécut), sexe (homme, femme), âge (adulte, enfant) et classe (première, deuxième, troisième, équipage).

Les rubans de survie sont colorés, une couleur pour les survivants et une autre pour les victimes, si bien qu'une combinaison se suit d'un bout à l'autre du diagramme. Le nœud « péri puis homme » regroupe 1 364 passagers, soit 62 % de l'effectif total.

Trois opérations accompagnent la lecture : changer la variable ou la catégorie mise en avant (*Change*), sélectionner un sous-ensemble (*Select*), et naviguer entre les niveaux (*Navigate*).

# Remarque

Le diagramme ne convient qu'aux données catégorielles : il encode des effectifs par des largeurs, pas des valeurs quantitatives continues. Il relève des [[Types de jeux de données]] tabulaires, dont il montre les dépendances entre attributs, à la différence de la [[Représentation visuelle des réseaux]], qui encode des liens entre items.

Le changement, la sélection et la navigation en font un cas d'application de la [[Manipulation d'une visualisation]].

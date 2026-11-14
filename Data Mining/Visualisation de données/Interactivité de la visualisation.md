#dmv-visualization

# Interprétation

Sur de grands jeux de données, ni l'utilisateur ni l'affichage ne permettent de montrer l'ensemble des données en une seule fois : le nombre de dimensions et le nombre d'observations dépassent ce qu'une figure peut porter.

Une vue statique ne donne qu'une seule vue d'un nombre limité de dimensions : elle fige un choix d'axes, de variables et d'ordre. Or le même jeu de données peut être trié selon plusieurs critères, et chaque tri fait apparaître d'autres structures. L'interaction est ce qui donne accès à cette succession de vues : elle transforme une figure unique en parcours d'exploration.

# Exemple

Le nuage de points du revenu par habitant en fonction de l'espérance de vie se lit différemment selon l'année affichée, le tri des points et les variables mises en avant : la même table de données supporte une série de vues qui ne se substituent pas l'une à l'autre.

La décomposition d'un graphique en couches (données, transformations statistiques, marques, échelles, coordonnées, facettes) décrit comment ces variantes se construisent à partir d'une même spécification : changer une couche suffit à obtenir une autre vue, ce qui rend l'exploration interactive réalisable.

Une galerie de vues proposées pour un même jeu de données illustre le même principe : l'utilisateur compare des vues concurrentes au lieu d'en produire une seule.

# Remarque

L'interactivité ne se réduit pas au changement d'année ou de tri : elle suppose que l'utilisateur puisse agir sur la représentation elle-même, ce que décrivent la [[Manipulation d'une visualisation]] et les [[Vues multiples coordonnées]]. Elle est le retour de la [[Boucle du système de visualisation]], sans lequel la vue reste statique.

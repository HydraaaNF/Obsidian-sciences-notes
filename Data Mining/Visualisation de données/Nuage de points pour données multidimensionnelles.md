#dmv-visualization

# Modèle

Le nuage de points représente ici une table de $N$ pays par $T$ instants : chaque pays fournit une marque, chaque instant une étape de l'animation, et les attributs sont portés par la marque, sa position et sa couleur.

Les attributs sont donc répartis sur les deux axes et sur la couleur, la dimension temporelle étant portée par l'animation plutôt que par un axe.

# Exemple

Le nuage de l'espérance de vie et du revenu par habitant :

- axe des ordonnées : espérance de vie, en années ;
- axe des abscisses : revenu par habitant, corrigé de l'inflation, en dollars ;
- couleur : des groupes de pays, continents ou régions, plusieurs pays partageant une même teinte parmi le bleu, l'orange, le brun, le violet, le rouge, le vert et le jaune ;
- animation : un cercle de rayon variable se déplace d'un instant au suivant, le rayon figurant la population, et une étiquette marque l'année courante.

Une vue statique ne permet qu'une seule vue d'un nombre limité de dimensions : sur ce graphique, elle se réduit à l'instantané d'une année.

# Interprétation

Le graphique étend le [[Nuage de points|nuage de points]] à deux variables à une table complète : deux attributs quantitatifs sont portés par les positions, un regroupement de pays par la couleur, et l'animation ajoute le temps.

L'[[Interactivité de la visualisation|interactivité]] joue ici le rôle de dimension supplémentaire : elle permet de parcourir les instants et de trier le même jeu selon d'autres critères.

# Remarque

Le même graphique est décrit ailleurs comme portant trois attributs qualitatifs, alors que ses axes portent deux variables quantitatives, l'espérance de vie et le revenu par habitant, et que la couleur ne fait que répartir les pays en groupes de teintes : les deux descriptions coexistent.

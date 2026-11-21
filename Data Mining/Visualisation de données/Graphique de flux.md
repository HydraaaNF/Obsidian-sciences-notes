#dmv-visualization

# Définition

Un **graphique de flux** (streamgraph) est un graphique en aires empilées : une bande par catégorie, l'épaisseur d'une bande à un instant donné représentant la valeur de la catégorie à cet instant, et l'empilement des bandes donnant la composition du total au fil du temps.

# Exemple

La fréquence des prénoms commençant par la lettre P, par million de naissances, des années 1880 à 2016 : une bande par prénom (Pamela, Patricia, Patsy, Patrick, Paul, Paula, Parker, Pauline, Peggy, Peter, Pearl, Philip, Phyllis), l'épaisseur de la bande donnant la fréquence du prénom pour chaque année.

Le jeu de données tient en une table à une dimension temporelle, un attribut catégoriel (le prénom) et un attribut quantitatif (la fréquence par million de naissances). L'outil sépare les prénoms masculins et féminins et propose les rangs courants 1, 25, 100, 500 et 1000.

# Remarque

Le graphique de flux est un cas particulier de la [[Séparer les marques sans recouvrement|séparation des marques]] : les bandes ne se recouvrent pas et leur épaisseur remplace la superposition.

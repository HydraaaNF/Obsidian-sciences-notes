#dmv-visualization

# Modèle

ColorBrewer fournit des guides d'usage de la couleur pour la représentation de données, organisés en jeux de palettes :

- palettes séquentielles, pour un attribut ordonné qui croît d'un extrême à l'autre
- palettes divergentes, pour un attribut ordonné de part et d'autre d'une valeur neutre
- palettes qualitatives, pour un attribut catégoriel sans ordre

Chaque jeu se décline par le nombre de classes de données retenues et par le type de schéma, à teintes multiples ou à teinte unique.

# Interprétation

Le choix d'une palette se règle en trois temps :

- fixer le nombre de classes de données, donc la finesse de la lecture voulue
- choisir la famille de palette selon la [[Attribut et types d'attributs|direction d'ordre de l'attribut]] : croissante, divergente ou sans ordre
- filtrer les schémas selon les contraintes d'usage, la lisibilité pour les daltoniens, l'impression et la photocopie

S'y ajoutent les réglages de contexte cartographique (routes, villes, frontières), de fond, de transparence, et l'export des codes couleur au format hexadécimal pour les reports dans un outil de dessin.

# Remarque

Une palette ne compense pas un mauvais choix de canal : elle règle la répartition des teintes, pas leur discriminabilité. Les composantes de la couleur et la sensibilité de l'œil à chacune sont décrites dans [[Encodage par la couleur]], et leur classement dans les [[Canaux visuels et efficacité d'encodage|canaux visuels]].

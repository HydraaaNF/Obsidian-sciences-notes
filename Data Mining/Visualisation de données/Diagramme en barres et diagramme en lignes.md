#dmv-visualization

# Interprétation

Le choix entre barres et lignes dépend de la nature de l'axe des abscisses, donc du [[Attribut et types d'attributs|type de l'attribut]] qui y est porté :

- pour des catégories discrètes, le diagramme en barres est la représentation appropriée
- pour des intervalles continus ou ordonnés, le diagramme en lignes est valide et traduit la tendance ou le changement d'un intervalle au suivant

Relier deux catégories par une ligne suggère à tort un continuum, ou une transition, là où il n'y en a pas.

# Exemple

Tailles en pouces comparées selon deux découpages :

- femmes contre hommes : les barres conviennent, alors que la ligne qui relie le groupe des femmes à celui des hommes est incorrecte, car elle invente un passage continu d'un groupe à l'autre
- enfants de 10 ans contre enfants de 12 ans : les barres restent valides, et la ligne l'est aussi, car l'âge forme un intervalle ordonné dont la ligne traduit l'évolution

# Remarque

Le piège est donc dans l'axe, pas dans la forme : une ligne tracée sur un attribut catégoriel fabrique une pente qui n'a pas de sens, alors qu'une pente sur un attribut ordonné est une lecture légitime de la variation. Le même raisonnement gouverne le choix des marques séparées sans recouvrement, voir [[Séparer les marques sans recouvrement]], et se paie dans le classement des [[Canaux visuels et efficacité d'encodage|canaux visuels]] par leur efficacité.

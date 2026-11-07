#adm-9

# Définition

La table de la loi normale centrée réduite associe à une valeur $u$ la probabilité cumulée

$$F(u) = \mathbb{P}[Z \leq u]$$

où $Z$ suit la [[Loi gaussienne|loi normale centrée réduite]] $\mathcal{N}(0,1)$. Les valeurs sont rangées par lignes et colonnes : la partie entière et la première décimale de $u$ repèrent la ligne, la deuxième décimale repère la colonne.

| $u$ | 0,00 | 0,01 | 0,02 | 0,03 | 0,04 | 0,05 | 0,06 | 0,07 | 0,08 | 0,09 |
|---|---|---|---|---|---|---|---|---|---|---|
| 0,0 | 0,5000 | 0,5040 | 0,5080 | 0,5120 | 0,5160 | 0,5199 | 0,5239 | 0,5279 | 0,5319 | 0,5359 |
| 0,1 | 0,5398 | 0,5438 | 0,5478 | 0,5517 | 0,5557 | 0,5596 | 0,5636 | 0,5675 | 0,5714 | 0,5753 |
| 0,2 | 0,5793 | 0,5832 | 0,5871 | 0,5910 | 0,5948 | 0,5987 | 0,6026 | 0,6064 | 0,6103 | 0,6141 |
| 0,3 | 0,6179 | 0,6217 | 0,6255 | 0,6293 | 0,6331 | 0,6368 | 0,6406 | 0,6443 | 0,6480 | 0,6517 |
| 0,4 | 0,6554 | 0,6591 | 0,6628 | 0,6664 | 0,6700 | 0,6736 | 0,6772 | 0,6808 | 0,6844 | 0,6879 |
| 0,5 | 0,6915 | 0,6950 | 0,6985 | 0,7019 | 0,7054 | 0,7088 | 0,7123 | 0,7157 | 0,7190 | 0,7224 |
| 0,6 | 0,7257 | 0,7290 | 0,7324 | 0,7357 | 0,7389 | 0,7422 | 0,7454 | 0,7486 | 0,7517 | 0,7549 |
| 0,7 | 0,7580 | 0,7611 | 0,7642 | 0,7673 | 0,7704 | 0,7734 | 0,7764 | 0,7794 | 0,7823 | 0,7852 |
| 0,8 | 0,7881 | 0,7910 | 0,7939 | 0,7967 | 0,7995 | 0,8023 | 0,8051 | 0,8078 | 0,8106 | 0,8133 |
| 0,9 | 0,8159 | 0,8186 | 0,8212 | 0,8238 | 0,8264 | 0,8289 | 0,8315 | 0,8340 | 0,8365 | 0,8389 |

Les probabilités sont données avec quatre décimales.

# Modèle

L'emploi de la table exige la standardisation préalable de la valeur dont on veut connaître la probabilité cumulée. Pour une observation $x_i$ d'une variable d'écart type $\sigma$ et de moyenne empirique $\bar{x}$, la valeur standardisée vaut

$$u = \frac{x_i - \bar{x}}{\sigma}.$$

La lecture suit une convention fixe : $u$ se lit dans la première colonne pour sa partie entière et sa première décimale, la deuxième décimale se trouvant dans la première ligne. La probabilité cumulée est lue à l'intersection de la ligne et de la colonne ainsi repérées.

# Algorithme

1. Calculer la valeur standardisée $u = \dfrac{x_i - \bar{x}}{\sigma}$.
1. Repérer dans la première colonne la ligne portant la partie entière et la première décimale de $u$.
1. Repérer dans la première ligne la colonne portant la deuxième décimale de $u$.
1. Lire à l'intersection la probabilité cumulée $F(u)$.

# Interprétation

La courbe en cloche de la loi normale centrée réduite est découpée en deux zones par la verticale d'abscisse $u$ : la zone hachurée, à gauche de $u$, s'étend de $-\infty$ jusqu'à $u$, et son aire vaut exactement $F(u)$. La table ne donne donc rien d'autre que l'aire sous la densité à gauche de la valeur standardisée, c'est-à-dire la probabilité que la variable reste inférieure ou égale à cette valeur.

# Exemple

Pour $u = 0{,}16$, la ligne est celle de $0{,}1$ et la colonne celle de $0{,}06$ : la table donne $F(0{,}16) = 0{,}5636$. Pour $u = 0{,}05$, la ligne est celle de $0{,}0$ et la colonne celle de $0{,}05$ : $F(0{,}05) = 0{,}5199$.

# Remarque

La table est tabulée pour $u \geq 0$ ; les valeurs négatives s'en déduisent par la symétrie de la loi normale centrée réduite, $\mathbb{P}[Z \leq -u] = 1 - \mathbb{P}[Z \leq u]$.

Le même principe de lecture à double entrée sert pour les autres tables usuelles : celle de la [[Loi de Student|loi de Student]], celle de la [[Loi du chi-deux|loi du chi-deux]] et celle de la [[Loi de Fisher|loi de Fisher]], où les degrés de liberté s'ajoutent en en-tête et où la valeur tabulée est un quantile et non une probabilité cumulée.

C'est cette lecture qui fournit le seuil de décision dans un [[Test de comparaison d'une moyenne à une valeur donnée|test de comparaison d'une moyenne à une valeur donnée]] ; le [[Quantile de la loi normale centrée réduite|quantile de la loi normale centrée réduite]] s'obtient de la même façon, en cherchant dans la table la probabilité cumulée voulue.

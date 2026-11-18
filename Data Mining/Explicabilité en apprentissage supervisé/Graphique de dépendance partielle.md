#dmv-xai

# Définition

Un **graphique de dépendance partielle** (PDP, *partial dependence plot*) représente l'effet marginal de caractéristiques sur les réponses d'un modèle opaque : la prédiction est tracée en fonction des valeurs d'une ou deux caractéristiques, la contribution des autres étant moyennée.

Soit $S$ l'ensemble des caractéristiques retenues et $C$ son complémentaire. La dépendance partielle de la prédiction $\hat{f}$ au point $x_S$ est l'espérance de $\hat{f}(x_S, X_C)$ sur la loi de $X_C$ :

$$\hat{f}_S(x_S) = \mathbb{E}_{X_C}\left[\hat{f}(x_S, X_C)\right] = \int \hat{f}(x_S, X_C) \, d\mathbb{P}(X_C)$$

En pratique, cette espérance est estimée par une moyenne empirique sur les $n$ observations disponibles :

$$\hat{f}_S(x_S) = \frac{1}{n}\sum_{i=1}^{n} \hat{f}\left(x_S, x_C^{(i)}\right)$$

où $x_C^{(i)}$ désigne les valeurs des caractéristiques complémentaires dans la $i$-ème observation.

# Interprétation

La courbe obtenue se lit comme la réponse moyenne du modèle lorsqu'on impose une valeur à la caractéristique étudiée, sans toucher aux autres : une pente forte signale une caractéristique influente, un plateau une zone où la prédiction ne varie plus.

Pour deux caractéristiques, la dépendance partielle se lit sur une **carte de chaleur** : chaque cellule donne la prédiction moyenne pour une combinaison de valeurs, et l'échelle de couleur va des valeurs basses (violet foncé) aux valeurs hautes (jaune).

# Exemple

**Modèle de location de vélos en libre-service.** Les trois courbes partagent un axe des ordonnées intitulé « nombre prédit de vélos », dont les graduations portent 0, 2 000 et 4 000 : l'échelle s'étend au-delà de 4 000 et les courbes culminent vers 5 000.

| Caractéristique | Axe des abscisses | Allure de la courbe |
|---|---|---|
| Température | 0 à 30 °C | hausse d'environ 3 450 à 0 °C jusqu'à un plateau d'environ 5 000 entre 15 et 25 °C, puis légère décroissance jusqu'à environ 4 850 |
| Humidité | 0 à 100 % | prédiction haute (environ 4 650) jusqu'à environ 55 %, puis chute jusqu'à environ 3 750 vers 100 % |
| Vitesse du vent | 0 à 30 | décroissance d'environ 4 600 à environ 4 500 vers 15, puis baisse jusqu'à environ 4 100 vers 25 et stabilisation |

**Carte de chaleur de l'âge et du nombre de grossesses.** Une seconde illustration, portant sur un autre jeu de données que les courbes, croise l'âge (en abscisse, d'environ 15 à 85) et le nombre de grossesses (en ordonnée, de 0 à 9). Son échelle de valeurs va de 0,050 (violet foncé) à 0,125 (jaune) ; elle ne compte pas de vélos et ne se rapporte pas aux ordonnées des courbes.

| Zone de la carte | Valeur relative |
|---|---|
| bord gauche, âges inférieurs à 20 ans, vers 3 à 4 grossesses | maximale (jaune) |
| bande d'environ 45 à 55 ans, surtout de 0 à 5 grossesses | maximale (jaune) |
| âges d'environ 30 à 45 ans, pour la plupart des nombres de grossesses | minimale (violet foncé) |

# Remarque

Deux limites expliquent le recours à d'autres outils d'inspection :

- la **dimensionnalité** : au-delà de deux caractéristiques la représentation devient illisible ;
- l'**indépendance** : l'estimation moyenne sur la loi de $X_C$ suppose que les caractéristiques retenues et les caractéristiques complémentaires ne sont pas liées.

Les valeurs données en exemple sont relevées sur les figures. Une lecture qui s'arrête aux trois graduations imprimées (0, 2 000, 4 000) place ces courbes plus bas, comme si l'axe s'arrêtait à 4 000 : la température partirait alors d'environ 1 200 à 0 °C, le plateau serait vers 4 500 et l'humidité finirait vers 3 000. La figure montre un départ vers 3 450 à 0 °C, un plateau vers 5 000 et une humidité qui finit vers 3 750 ; c'est cette lecture qui est retenue.

De même, les cellules de la carte situées vers 20 à 30 ans avec 2 à 3 grossesses vont du violet au vert, alors que les valeurs maximales se lisent ailleurs : les taches jaunes se lisent au bord gauche, avant 20 ans vers 3 à 4 grossesses, et dans une bande d'environ 45 à 55 ans.

D'autres techniques d'inspection de la boîte noire complètent les PDP :

- l'analyse de sensibilité ;
- les graphiques d'espérance conditionnelle individuelle (*Individual Conditional Expectation*, ICE), qui tracent une courbe par observation au lieu d'une moyenne ;
- les graphiques d'effets locaux accumulés (*Accumulated Local Effects*, ALE), qui remplacent la moyenne globale par des différences locales.

Les PDP sont une méthode d'[[Explication globale]], à contraster avec l'[[Explication locale]] qui décrit une prédiction individuelle : elles s'apparentent à l'[[Importance des variables par agrégation]] et se rangent aux côtés des [[Contrefactuels globaux]] parmi les explications globales. La lecture d'une carte de chaleur à deux variables rejoint la recherche d'[[Interprétabilité]] du modèle.

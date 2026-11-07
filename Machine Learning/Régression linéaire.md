#ml-1

# Modèle

On dispose d'un ensemble de points de données $(x, y)$ et on cherche une fonction $f$ telle que $f(x)$ soit aussi proche que possible de $y$. Cette exigence de proximité est exactement ce que mesure une perte : le problème se ramène donc à choisir $f$ en minimisant une [[Perte absolue et perte quadratique|perte]] sur les données observées.

La régression linéaire restreint ce choix aux fonctions affines.

# Définition

Une fonction affine de paramètres $a$ et $b$ s'écrit

$$f_{a,b}(x) = ax + b = \hat{y},$$

où $\hat{y}$ est la prédiction.

La perte $\ell$ d'une paire $(x, y)$ compare la prédiction $\hat{y} = f(x)$ à la vérité terrain $y$. Les deux pertes usuelles sont :

- l'erreur absolue : $\ell(\hat{y}, y) = |\hat{y} - y|$ ;
- l'erreur quadratique : $\ell(\hat{y}, y) = (\hat{y} - y)^2$.

La perte totale sur le jeu de données est

$$L(a, b) = \sum_i \ell(f_{a,b}(x_i), y_i).$$

La régression linéaire cherche le couple de paramètres qui minimise cette perte sur les données observées :

$$(a^*, b^*) = \operatorname*{argmin}_{(a,b)} L(a, b).$$

# Remarque

- $L$ est une fonction des paramètres, pas des données : les points $(x_i, y_i)$ sont fixés, et ce sont $a$ et $b$ que l'on fait varier.
- La recherche de $(a^*, b^*)$ est un problème d'optimisation. Pour ce modèle, il admet une solution fermée, mais la [[Descente de gradient]] lui est préférée : elle reste applicable à tous les modèles qui suivent.
- La régression linéaire est le cas linéaire de la [[Courbe de régression]] : on y ajuste une fonction affine au nuage de points, au sens des moindres carrés.
- La solution fermée est donnée par la [[Droite de régression de y en x|droite de régression de y en x]], dite droite des moindres carrés : ses coefficients se calculent directement à partir des moyennes, de la covariance et de la variance des observations.
- La démarche se transpose à d'autres modèles : on y minimise toujours une perte sur les données observées, et la même descente de gradient résout le problème ; seule la perte change.

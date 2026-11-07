#adm-8

# Définition

Soit une variable $X$ prenant ses valeurs dans $\{x_1, \dots, x_n\}$, et $m$ fonctions de traits mesurables $f_1, \dots, f_m$ dont les espérances sous la distribution de $X$ sont fixées par les faits connus, sous la forme des [[Contraintes d'espérance sur les fonctions de traits|contraintes d'espérance]] portant sur ces fonctions.

La distribution de maximum d'entropie de $X$, au sens du [[Principe du maximum d'entropie]], a la forme exponentielle

$$\mathbb{P}[X = x_k] = \frac{1}{Z} \exp\left( \sum_{j=1}^{m} \lambda_j f_j(x_k) \right)$$

pour tout $k = 1, \dots, n$. Les paramètres $\lambda_j$ sont déterminés de façon à vérifier les contraintes, et sont donc liés aux espérances $F_k$ fixées ; $Z$ est une fonction normalisatrice, encore appelée fonction de partition, donnée par

$$Z = \sum_{i=1}^{n} \exp\left( \sum_{j=1}^{m} \lambda_j f_j(x_i) \right).$$

# Interprétation

À chaque valeur $x_k$ la forme exponentielle associe un score $s(x_k) = \sum_{j=1}^{m} \lambda_j f_j(x_k)$, combinaison linéaire des valeurs prises par les fonctions de traits en $x_k$, puis convertit ce score en probabilité par une exponentielle, avant de renormaliser par $Z$.

Le poids de chaque fonction de trait dans le score est son multiplicateur $\lambda_j$ :

- un coefficient $\lambda_j$ positif renforce la probabilité des valeurs $x_k$ où $f_j(x_k)$ est grande ;
- un coefficient $\lambda_j$ négatif la réduit ;
- un coefficient nul annule l'influence de la fonction de trait correspondante.

La distribution obtenue ne dépend donc que des faits traduits en contraintes : les fonctions de traits qui ne sont pas contraintes reçoivent un coefficient nul et n'introduisent aucun biais.

# Propriétés

La fonction de partition normalise bien la distribution, puisque la somme des probabilités vaut

$$\sum_{k=1}^{n} \mathbb{P}[X = x_k] = \frac{1}{Z} \sum_{k=1}^{n} \exp\left( \sum_{j=1}^{m} \lambda_j f_j(x_k) \right) = 1 .$$

Sans aucune contrainte active, c'est-à-dire lorsque tous les coefficients $\lambda_j$ sont nuls, chaque score est nul et $Z = n$ : la forme exponentielle redonne la [[Loi uniforme discrète|loi uniforme discrète]] sur $\{x_1, \dots, x_n\}$, qui est la distribution d'entropie maximale en l'absence d'information.

# Remarque

La forme obtenue est celle d'une [[Distribution de Gibbs]] : un produit de facteurs exponentiels divisé par une constante de normalisation, la seule particularité du cas de maximum d'entropie étant que l'argument de l'exponentielle est une combinaison linéaire des fonctions de traits.

Dans un modèle conditionnel, la même fonction de partition apparaît en sommant sur les étiquettes plutôt que sur les valeurs de $X$ ; pour un [[Champ aléatoire conditionnel à chaîne linéaire]] elle s'écrit $Z(x, \Lambda) = \sum_{y} \exp\left( \sum_{i=1}^{m} \lambda_i f_i(x, y) \right)$, où $y$ parcourt les séquences d'étiquettes possibles.

Les multiplicateurs $\lambda_j$ ne sont pas choisis librement : ils sont ajustés pour que les contraintes soient vérifiées, ce qui donne lieu à l'[[Estimation des paramètres par les multiplicateurs de Lagrange|estimation par les multiplicateurs de Lagrange]].

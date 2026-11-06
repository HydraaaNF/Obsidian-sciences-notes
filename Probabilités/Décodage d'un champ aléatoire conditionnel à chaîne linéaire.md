# Définition

Décoder un [[Champ aléatoire conditionnel à chaîne linéaire|champ aléatoire conditionnel à chaîne linéaire]] consiste, pour une suite d'observations $x$ fixée, à trouver la suite d'étiquettes $\hat{y}$ qui maximise la probabilité a posteriori du modèle, une [[Distribution de Gibbs|distribution de Gibbs]] :

$$\hat{y} = \arg\max_{y} \frac{1}{Z(x, \Lambda)} \exp\left( \sum_{i=1}^{m} \lambda_i f_i(x, y) \right)$$

Le maximum porte sur toutes les suites d'étiquettes $y = (y_1, \dots, y_n)$ possibles, et non sur une étiquette position par position : la suite retenue est la plus probable dans son ensemble. Les [[Fonctions de traits pour les séquences|fonctions de traits]] $f_i$ sont pondérées par les paramètres $\Lambda = \{\lambda_1, \dots, \lambda_m\}$, et $Z(x, \Lambda)$ désigne la fonction de partition du modèle.

# Propriétés

Deux simplifications successives laissent la suite $\hat{y}$ inchangée. La fonction de partition, d'abord, ne dépend que des observations $x$ et des paramètres $\Lambda$ : elle est constante dans la comparaison des suites candidates et disparaît de l'argument du maximum.

$$\hat{y} = \arg\max_{y} \sum_{i=1}^{m} \lambda_i f_i(x, y)$$

L'exponentielle, ensuite, est strictement croissante : maximiser $\exp(s)$ revient à maximiser $s$, si bien que le décodage se ramène à la maximisation du seul score $\sum_{i=1}^{m} \lambda_i f_i(x, y)$.

La [[Décomposition positionnelle des fonctions de traits|décomposition positionnelle]] des fonctions de traits, $f_i(x, y) = \sum_{s=1}^{n} f_i(y_{s-1}, y_s, x, s)$, permet d'écrire ce score comme une somme de contributions locales et de réordonner les deux sommes :

$$\hat{y} = \arg\max_{y} \sum_{s=1}^{n} g_s(y_{s-1}, y_s)$$

où le score local de la position $s$ vaut

$$g_s(y_{s-1}, y_s) = \sum_{i=1}^{m} \lambda_i f_i(y_{s-1}, y_s, x, s)$$

Le score global à maximiser est donc une somme de $n$ termes, un par position, chacun ne dépendant que du couple d'étiquettes consécutives $(y_{s-1}, y_s)$.

# Interprétation

Décoder revient à choisir, parmi les suites d'étiquettes, celle dont le score additif est le plus grand. Chaque position apporte sa contribution $g_s$, qui se lit sur les observations et sur le couple d'étiquettes qu'elle relie à la précédente : le score se parcourt le long de la chaîne, comme le score d'un chemin dans un [[Treillis|treillis]].

La structure locale de la somme rend le maximum calculable sans énumérer les suites candidates : le meilleur chemin se construit de proche en proche par [[Programmation dynamique pour un champ aléatoire conditionnel|programmation dynamique]], de la même façon que le [[Décodage d'une séquence d'états|décodage d'une séquence d'états]] d'un [[Modèle de Markov caché]] par l'[[Algorithme de Viterbi]].

La disparition de la fonction de partition est ce qui rend le décodage économique : $Z(x, \Lambda)$ est une somme sur toutes les suites d'étiquettes possibles, et cette somme n'a pas à être évaluée pour trouver $\hat{y}$.

# Remarque

La seconde simplification conserve l'$\arg\max$ : la quantité $\sum_{s=1}^{n} g_s(y_{s-1}, y_s)$ est un score, un nombre réel attaché à une suite candidate, et non la suite elle-même. La forme à retenir est donc

$$\hat{y} = \arg\max_{y} \sum_{s=1}^{n} g_s(y_{s-1}, y_s)$$

L'écriture $\hat{y} = \sum_{s=1}^{n} g_s(y_{s-1}, y_s)$ est une erreur fréquente : elle identifie le résultat du décodage (une suite d'étiquettes) au maximum du score (un nombre), alors que les deux objets sont de natures différentes.

Les deux simplifications reposent sur la même propriété : l'$\arg\max$ ne retient que l'ordre des valeurs comparées, ordre que ni la division par la constante $Z(x, \Lambda)$ ni l'exponentielle ne modifient.

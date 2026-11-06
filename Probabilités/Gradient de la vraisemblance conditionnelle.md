Le [[Vraisemblance conditionnelle d'un champ aléatoire conditionnel|maximum de vraisemblance conditionnelle]] d'un [[Champ aléatoire conditionnel à chaîne linéaire|champ aléatoire conditionnel]] n'a pas de solution analytique : on maximise l'objectif par montée de gradient, ce qui demande d'exprimer la dérivée partielle de la log-vraisemblance par rapport à chaque paramètre $\lambda_i$.

# Propriétés

Pour un exemple unique $(x, y)$, la dérivée de la log-vraisemblance conditionnelle par rapport à $\lambda_i$ est la différence entre la valeur du trait sur l'étiquetage observé et son espérance sous la loi conditionnelle courante :

$$
\frac{\partial}{\partial \lambda_i} \ln \mathbb{P}[y \mid x; \Lambda] = f_i(x, y) - \mathbb{E}\left[ f_i(x, Y) \mid x; \Lambda \right]
$$

En développant l'espérance à l'aide de la [[Distribution de Gibbs|forme de Gibbs]] et de la fonction de partition, il vient

$$
\frac{\partial}{\partial \lambda_i} \ln \mathbb{P}[y \mid x; \Lambda] = f_i(x, y) - \frac{1}{Z(x, \Lambda)} \sum_{y'} f_i(x, y') \exp\left( \sum_j \lambda_j f_j(x, y') \right)
$$

Sur l'ensemble du jeu d'apprentissage, la dérivée est la somme des dérivées par exemple ; en notant $\ell(\Lambda)$ la log-vraisemblance du corpus,

$$
\frac{\partial \ell}{\partial \lambda_i} = \sum_{r} \left( f_i(x^{(r)}, y^{(r)}) - \mathbb{E}\left[ f_i(x, Y) \mid x^{(r)}; \Lambda \right] \right)
$$

Annuler ces dérivées pour tous les paramètres donne les conditions du premier ordre du maximum de vraisemblance conditionnelle : pour chaque trait $i$, l'[[Espérance empirique d'une fonction de trait|espérance empirique]] du trait sur les données égale son espérance théorique sous le modèle estimé.

$$
\sum_{r} f_i(x^{(r)}, y^{(r)}) = \sum_{r} \mathbb{E}\left[ f_i(x, Y) \mid x^{(r)}; \hat{\Lambda} \right]
$$

### Démonstration

La log-vraisemblance d'un exemple sépare le score des étiquettes observées et le logarithme de la fonction de partition, dont seul le second dépend de $\lambda_i$ de façon non triviale :

$$
\frac{\partial}{\partial \lambda_i} \ln \mathbb{P}[y \mid x; \Lambda] = f_i(x, y) - \frac{\partial}{\partial \lambda_i} \ln Z(x, \Lambda)
$$

La dérivée du logarithme se ramène à celle de la fonction de partition :

$$
\frac{\partial}{\partial \lambda_i} \ln \mathbb{P}[y \mid x; \Lambda] = f_i(x, y) - \frac{1}{Z(x, \Lambda)} \frac{\partial}{\partial \lambda_i} Z(x, \Lambda)
$$

Or $Z(x, \Lambda)$ est une somme d'exponentielles, que l'on dérive terme à terme ; la dérivée de $\exp\left( \sum_j \lambda_j f_j(x, y) \right)$ par rapport à $\lambda_i$ vaut $f_i(x, y)$ fois l'exponentielle elle-même, d'où

$$
\frac{\partial}{\partial \lambda_i} Z(x, \Lambda) = \sum_{y'} f_i(x, y') \exp\left( \sum_j \lambda_j f_j(x, y') \right)
$$

En reportant cette expression dans la dérivée du logarithme, le quotient obtenu est exactement l'espérance de $f_i(x, Y)$ sous la loi conditionnelle $\mathbb{P}[Y \mid x; \Lambda]$ :

$$
\frac{\partial}{\partial \lambda_i} \ln \mathbb{P}[y \mid x; \Lambda] = f_i(x, y) - \frac{1}{Z(x, \Lambda)} \sum_{y'} f_i(x, y') \exp\left( \sum_j \lambda_j f_j(x, y') \right)
$$

# Interprétation

Le gradient compare deux quantités pour chaque trait.

- $f_i(x, y)$ est la valeur du trait sur l'étiquetage réellement observé : c'est, sommé sur le corpus, l'espérance empirique du trait.
- $\mathbb{E}\left[ f_i(x, Y) \mid x; \Lambda \right]$ est la valeur moyenne du même trait sur tous les étiquetages que le modèle courant juge possibles : c'est l'espérance théorique.

Le signe du gradient indique donc le sens de la correction à appliquer. Si le trait est plus actif sur les annotations que le modèle ne le prévoit, la dérivée est positive et la montée de gradient augmente $\lambda_i$ : le modèle doit mieux noter ces configurations. Si le modèle sur-emploie le trait, la dérivée est négative et $\lambda_i$ diminue.

À l'optimum, ces deux quantités se compensent trait par trait : le modèle reproduit les fréquences des fonctions de traits observées dans les annotations, sans pouvoir les dépasser. Ce mécanisme est celui de l'[[Estimation des paramètres par les multiplicateurs de Lagrange|estimation par les multiplicateurs de Lagrange]], où les contraintes d'espérance jouent le même rôle.

# Remarque

L'égalité entre espérance empirique et espérance théorique porte sur l'ensemble des données d'apprentissage, jamais sur un point isolé : sur un exemple unique, $f_i(x, y)$ n'a aucune raison d'égaler son espérance sous le modèle, et c'est seulement en sommant sur tous les exemples que les écarts se compensent. L'équilibre est donc une propriété globale du corpus, pas une reproduction exacte de chaque annotation.

Le calcul de l'espérance théorique demande de sommer sur toutes les suites d'étiquettes possibles, dont le nombre croît exponentiellement avec la longueur de la séquence. Pour une chaîne linéaire, cette somme se factorise et s'évalue par l'[[Calcul des espérances par l'algorithme forward-backward|algorithme forward-backward]], ce qui rend la [[Entraînement d'un champ aléatoire conditionnel par gradient|montée de gradient]] praticable.

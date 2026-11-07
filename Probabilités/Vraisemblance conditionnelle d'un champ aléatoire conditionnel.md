#adm-8

# Définition

Un [[Champ aléatoire conditionnel à chaîne linéaire|champ aléatoire conditionnel]] définit la loi conditionnelle des étiquettes sachant les observations. Pour un exemple $(x, y)$ et des paramètres $\Lambda = \{\lambda_1, \dots, \lambda_m\}$, cette loi est la [[Distribution de Gibbs|distribution de Gibbs]]

$$
\mathbb{P}[y \mid x; \Lambda] = \frac{1}{Z(x; \Lambda)} \exp\left( \sum_{i=1}^{m} \lambda_i f_i(x, y) \right)
$$

où la fonction de partition vaut

$$
Z(x; \Lambda) = \sum_{y'} \exp\left( \sum_{i=1}^{m} \lambda_i f_i(x, y') \right)
$$

Sur un jeu d'apprentissage de $R$ exemples indépendants $(x^{(r)}, y^{(r)})$, la vraisemblance conditionnelle est le produit des probabilités attribuées aux étiquettes observées ; sa log-vraisemblance est

$$
\ell(\Lambda) = \sum_{r=1}^{R} \left( \sum_{i=1}^{m} \lambda_i f_i(x^{(r)}, y^{(r)}) - \ln Z(x^{(r)}; \Lambda) \right)
$$

L'estimation des paramètres par maximum de vraisemblance conditionnelle donne

$$
\hat{\Lambda} = \arg\max_{\Lambda} \sum_{r} \left( \sum_{i} \lambda_i f_i(x^{(r)}, y^{(r)}) - \ln Z(x^{(r)}; \Lambda) \right)
$$

# Interprétation

Deux termes s'opposent dans l'objectif.

- Le premier, $\sum_{i} \lambda_i f_i(x^{(r)}, y^{(r)})$, est le score attribué aux étiquettes réellement observées ; il croît linéairement avec les paramètres des traits qui comptent les configurations correctes. C'est, à un facteur près, l'[[Espérance empirique d'une fonction de trait|espérance empirique]] des fonctions de traits sur les étiquettes du jeu d'apprentissage.
- Le second, $\ln Z(x^{(r)}; \Lambda)$, est le logarithme du score total de toutes les suites d'étiquettes possibles ; il croît lui aussi avec les paramètres et joue le rôle de frein.

Maximiser la log-vraisemblance revient donc à rendre les annotations observées plus probables relativement à l'ensemble des étiquetages concurrents, et non à augmenter leur score absolu : sans le terme de normalisation, l'objectif serait non borné et les paramètres divergeraient.

# Propriétés

La log-vraisemblance conditionnelle est une fonction concave des paramètres (forme $\cap$), donc l'objectif opposé $-\ell$ est convexe.

L'objectif n'admet pas de solution analytique, comme toujours avec les [[Distribution de Gibbs|distributions de Gibbs]] : le logarithme de la fonction de partition mêle tous les paramètres à toutes les suites d'étiquettes, si bien que l'annulation du gradient conduit à un système que l'on ne sait pas résoudre explicitement.

La concavité jointe à l'absence de forme close impose une optimisation itérative : on maximise l'objectif par [[Entraînement d'un champ aléatoire conditionnel par gradient|montée de gradient]], ce qui suppose de calculer le [[Gradient de la vraisemblance conditionnelle|gradient de la vraisemblance conditionnelle]].

Sur le relief de l'objectif, les lignes de niveau se présentent en courbes fermées emboîtées autour du maximum ; une montée de gradient part d'un point quelconque, progresse par pas perpendiculaires aux lignes de niveau et se rapproche du centre en zigzag, les déplacements se raccourcissant à mesure que la pente diminue.

# Remarque

La factorisation de la vraisemblance en produit suppose les exemples indépendants ; c'est l'hypothèse usuelle sur un jeu d'apprentissage, elle n'est pas une propriété du modèle.

Seule la loi conditionnelle des étiquettes est modélisée : les observations $x$ sont traitées comme données, et leur loi n'a pas à être spécifiée, à la différence d'un modèle génératif de la paire $(X, Y)$ comme le [[Modèle de Markov caché]], dont l'estimation porte sur la vraisemblance jointe.

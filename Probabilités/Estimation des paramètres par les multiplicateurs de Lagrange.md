#adm-8

# Définition

Les paramètres d'une distribution de maximum d'entropie de [[Forme exponentielle d'une distribution de maximum d'entropie|forme exponentielle]] constituent l'ensemble $\Lambda = \{\lambda_1, \dots, \lambda_m\}$.

L'estimation $\widehat{\Lambda}$ est le jeu de multiplicateurs de Lagrange obtenu par le système d'équations

$$
F_k = \frac{\partial \ln Z(\Lambda)}{\partial \lambda_k}
$$

pour $k = 1, \dots, m$, où $F_k$ est la valeur imposée à l'espérance de la fonction de trait $f_k$ et $Z(\Lambda)$ la fonction de partition

$$
Z(\Lambda) = \sum_{i=1}^{n} \exp\left( \sum_{j=1}^{m} \lambda_j f_j(x_i) \right) .
$$

# Propriétés

La distribution cherchée s'écrit

$$
\mathbb{P}(X = x_i) = \frac{1}{Z(\Lambda)} \exp\left( \sum_{j=1}^{m} \lambda_j f_j(x_i) \right)
$$

et les faits observés imposent les $m$ [[Contraintes d'espérance sur les fonctions de traits|contraintes d'espérance]]

$$
\sum_{i=1}^{n} f_k(x_i) \mathbb{P}(X = x_i) = F_k .
$$

Le problème s'écrit donc comme la maximisation de l'entropie sous ces contraintes et sous la contrainte de somme à un. Le lagrangien associe un multiplicateur à chacune d'elles,

$$
\mathcal{L}(P, \Lambda, \mu) = -\sum_{i=1}^{n} P(x_i) \ln P(x_i) + \sum_{k=1}^{m} \lambda_k \left( \sum_{i=1}^{n} f_k(x_i) P(x_i) - F_k \right) + \mu \left( \sum_{i=1}^{n} P(x_i) - 1 \right) .
$$

L'annulation de sa dérivée par rapport à chaque probabilité $P(x_i)$ donne

$$
\frac{\partial \mathcal{L}}{\partial P(x_i)} = -\ln P(x_i) - 1 + \sum_{k=1}^{m} \lambda_k f_k(x_i) + \mu = 0 .
$$

En isolant $P(x_i)$ on obtient

$$
P(x_i) = \exp(\mu - 1) \exp\left( \sum_{k=1}^{m} \lambda_k f_k(x_i) \right) .
$$

Le facteur constant $\exp(\mu - 1)$ est la constante de normalisation : il vaut $1/Z(\Lambda)$, puisque les probabilités doivent sommer à un. La solution du programme est donc bien la forme exponentielle, et les multiplicateurs $\lambda_k$ sont exactement les paramètres du modèle.

La dérivée de $\ln Z(\Lambda)$ par rapport à $\lambda_k$ s'obtient par composition. D'abord

$$
\frac{\partial Z(\Lambda)}{\partial \lambda_k} = \sum_{i=1}^{n} f_k(x_i) \exp\left( \sum_{j=1}^{m} \lambda_j f_j(x_i) \right) .
$$

Puis, en divisant par $Z(\Lambda)$,

$$
\frac{\partial \ln Z(\Lambda)}{\partial \lambda_k} = \sum_{i=1}^{n} f_k(x_i) \frac{\exp\left( \sum_{j=1}^{m} \lambda_j f_j(x_i) \right)}{Z(\Lambda)} .
$$

Chaque terme du membre de droite est $f_k(x_i)$ multiplié par $\mathbb{P}(X = x_i)$ : la dérivée vaut donc $\mathbb{E}[f_k(X)]$. Les équations d'estimation $F_k = \partial \ln Z(\Lambda)/\partial \lambda_k$ ne sont ainsi que la réécriture des contraintes initiales $\mathbb{E}[f_k(X)] = F_k$ : choisir $\widehat{\Lambda}$ par ces équations revient à exiger que le modèle reproduise les espérances imposées par les faits observés.

Dans le cas conditionnel d'un modèle $p(y \mid x; \Lambda)$ normalisé par $Z(x, \Lambda)$, le même calcul mené à $x$ fixé donne

$$
\frac{\partial}{\partial \lambda_i} \ln p(y \mid x; \Lambda) = f_i(x, y) - \frac{1}{Z(x, \Lambda)} \sum_{y'} f_i(x, y') \exp\left( \sum_j \lambda_j f_j(x, y') \right) .
$$

En annulant cette dérivée sur l'ensemble des données d'entraînement, on obtient l'égalité entre espérance empirique et espérance théorique

$$
\sum_r f_i\left(x^{(r)}, y^{(r)}\right) = \sum_r \mathbb{E}\left[f_i(x, y) \mid x^{(r)}; \widehat{\Lambda}\right] .
$$

Cette condition du premier ordre est l'analogue conditionnel des équations d'estimation : elle fixe les multiplicateurs de Lagrange du [[Gradient de la vraisemblance conditionnelle|gradient de la vraisemblance conditionnelle]].

# Interprétation

Le jeu $\widehat{\Lambda}$ obtenu comme multiplicateurs de Lagrange maximise la log-vraisemblance conditionnelle dans les problèmes de classification. Estimation par maximum d'entropie et estimation par maximum de vraisemblance d'un modèle conditionnel coïncident donc : dans les deux cas, les paramètres sont ajustés pour que les espérances calculées sous le modèle égalent celles mesurées sur les données.

# Remarque

L'égalité entre espérance empirique et espérance théorique porte sur l'ensemble des données d'entraînement, et non sur un point isolé : c'est la somme des dérivées sur tout le corpus qui s'annule.

Le système $F_k = \partial \ln Z(\Lambda)/\partial \lambda_k$ n'a pas de solution analytique, comme c'est le cas général pour les distributions de Gibbs. La fonction objectif étant concave, on la maximise par montée de gradient, ce qui ramène l'estimation à l'égalisation progressive des espérances empiriques et théoriques.

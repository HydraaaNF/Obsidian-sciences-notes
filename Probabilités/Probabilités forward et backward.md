# Définition

Dans un [[Modèle de Markov caché]] de paramètres $\lambda_N(\theta_n)$, les espérances s'expriment en fonction de deux probabilités.

La **probabilité forward** est la probabilité d'observer $o_1$ jusqu'à $o_t$ et d'être dans l'état $i$ à l'instant $t$ :

$$\alpha_t(i) = \mathbb{P}\left[o_1,\ldots,o_t,S_t = i;\lambda_N(\theta_n)\right]$$

La **probabilité backward** est la probabilité d'observer $o_{t+1}$ jusqu'à $o_T$ sachant que l'état à l'instant $t$ est $i$ :

$$\beta_t(i) = \mathbb{P}\left[o_{t+1},\ldots,o_T \mid S_t = i;\lambda_N(\theta_n)\right]$$

# Propriétés

Pour tout instant $t$, la probabilité de la séquence d'observations $\mathbf{o}$ s'écrit

$$\mathbb{P}[\mathbf{o};\lambda_N(\theta)] = \sum_{i=1}^{N}\alpha_i(t)\beta_i(t) \quad \forall t \in [1,T]$$

# Remarque

- La probabilité forward se calcule récursivement par l'[[Algorithme forward]] et la probabilité backward par l'[[Algorithme backward]].
- Ces deux quantités servent au [[Calcul des espérances par l'algorithme forward-backward]].

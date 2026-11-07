#ml-1

# Propriétés

Dans un [[Réseau récurrent]], le gradient d'un état ancien vers l'état final traverse chaque pas intermédiaire. La [[Rétropropagation dans le temps|rétropropagation dans le temps]] compose donc les dérivées de chaque pas :

$$\frac{\partial h_T}{\partial h_1} = \frac{\partial h_T}{\partial h_{T-1}} \cdots \frac{\partial h_2}{\partial h_1}$$

Le facteur local d'un pas est

$$\frac{\partial h_t}{\partial h_{t-1}} = \operatorname{diag}\left(\tanh'(\cdot)\right) W_h$$

où $W_h$ est la matrice des poids de l'état et $\tanh'$ la dérivée de la tangente hyperbolique, appliquée composante par composante.

C'est la même matrice $W_h$ qui intervient $T - 1$ fois : le produit se comporte comme un nombre $a$ élevé à la puissance $T - 1$.

- $a < 1$ : le gradient **disparaît**, $0.9^{50} \approx 0.005$ ;
- $a > 1$ : il **explose**, $1.1^{50} \approx 117$ ;
- $\tanh' \le 1$ pousse vers la disparition.

La dérivée de la tangente hyperbolique vaut $\tanh'(z) = 1 - \tanh^2(z)$, d'où la majoration $\tanh'(z) \le 1$.

# Interprétation

- Disparition : les entrées anciennes ne reçoivent aucun gradient, donc le réseau n'apprend jamais à s'en servir.
- Explosion : un seul pas de taille démesurée détruit les poids.
- La disparition appelle une autre cellule, la [[Mémoire à long et court terme]].

# Remarque

- Remède à l'explosion : borner la norme du gradient avec `clip_grad_norm_`, entre `backward` et `step`.
- Conséquence sur l'[[Encodage d'une séquence|encodage d'une séquence]] : quand une séquence est résumée par son dernier état $e = h_T$, le début de la séquence est mal représenté, puisqu'il a traversé $T$ mises à jour.
- Le même produit de facteurs guette la profondeur d'un réseau à propagation avant ; les [[Connexions résiduelles]] y ajoutent un chemin direct pour le gradient.

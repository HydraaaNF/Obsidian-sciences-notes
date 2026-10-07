# Définition

Le risque peut être défini de manière plus générale à l'aide d'une [[Fonction de perte|fonction de perte]] (ou d'erreur) $l(t, \theta)$ : $l(\theta, t) = 0$ si et seulement si $t = \theta$. Le risque généralisé d'un [[Estimateur|estimateur]] $T$ du paramètre $\theta$ est l'espérance de cette perte :

$$R(T, \theta) = \mathbb{E}_{\theta}[l(T(X), \theta)].$$

# Exemple

Exemples de fonctions d'erreur :

- **erreur quadratique** :
  $$l(a, b) = (a - b)^2$$
- **erreur absolue** :
  $$l(a, b) = |a - b|$$
- **perte epsilon** ($\epsilon$-loss) :
  $$l(a, b) = 0 \text{ si } |a - b| < \epsilon$$

# Remarque

Pour la perte quadratique $l(a, b) = (a - b)^2$, le risque généralisé coïncide avec l'[[Erreur quadratique moyenne]] : $R(T, \theta) = \mathbb{E}_{\theta}[(T(X) - \theta)^2]$.

Malheureusement, minimiser directement le risque n'est possible que dans quelques cas très particuliers. Pour la comparaison de deux estimateurs, voir [[Comparaison d'estimateurs]].

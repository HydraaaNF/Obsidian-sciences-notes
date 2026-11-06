# Algorithme

Le principe de l'[[Algorithme d'espérance-maximisation|algorithme d'espérance-maximisation]] (EM) admet de nombreuses variantes lorsque l'étape E et/ou l'étape M ne sont pas réalisables en pratique :

- **EM de Monte-Carlo** : remplacer le calcul exact des quantités espérées par des approximations de Monte-Carlo obtenues à partir des paramètres courants.
- **EM généralisé** : augmenter simplement la [[Fonction auxiliaire de l'algorithme d'espérance-maximisation|fonction auxiliaire]] plutôt que de la maximiser, par exemple à l'aide d'un algorithme de gradient.
- **EM variationnel** : remplacer la fonction auxiliaire $Q$ par une approximation variationnelle plus simple, reposant sur une distribution factorielle $Q \simeq \prod_i Q_i$.

# Remarque

D'autres variantes existent au-delà de ces trois exemples.

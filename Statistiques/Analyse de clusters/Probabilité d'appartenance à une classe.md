# Définition

La **probabilité d'appartenance** de la $i$-ème observation à la classe $j$ est

$$\gamma_j(i) = \mathbb{P}_{\hat{\theta}}[Z_i = j \mid x_i] = \frac{\hat{\pi}_j\, p_{\hat{\theta}_j}(x_i)}{\sum_k \hat{\pi}_k\, p_{\hat{\theta}_k}(x_i)},$$

où $\hat{\theta}$ désigne l'estimation courante des paramètres.

# Interprétation

La variable latente $\gamma_j(i)$ indique l'appartenance à une classe telle qu'estimée à partir de l'estimation courante $\hat{\theta}$ des paramètres.

- $\mathbb{P}_{\hat{\theta}}[Z_i = j \mid x_i]$ est le **degré d'appartenance** de la $i$-ème observation à la classe $j$, compris dans $[0, 1]$ ;
- la maximisation repose sur des estimateurs standards fondés sur ce degré d'appartenance (estimateurs standards pondérés).

$\gamma_j(i)$ est aussi l'espérance conditionnelle de l'indicatrice d'appartenance $\mathbb{1}_{\{Z_i = j\}}$ ; c'est donc une probabilité conditionnelle.

# Remarque

$\gamma_j(i)$ est la grandeur calculée à l'étape E de l'[[Algorithme d'espérance-maximisation]] ; les estimateurs pondérés par ces degrés d'appartenance réalisent la maximisation de la [[Fonction auxiliaire de l'algorithme d'espérance-maximisation]]. Ces estimateurs sont explicités, pour un mélange gaussien, dans l'[[Espérance-maximisation pour un mélange de gaussiennes]].

La forme de $\gamma_j(i)$ est celle de la [[Formule de Bayes]] : le dénominateur $\sum_k \hat{\pi}_k\, p_{\hat{\theta}_k}(x_i)$ somme les termes associés à toutes les classes.

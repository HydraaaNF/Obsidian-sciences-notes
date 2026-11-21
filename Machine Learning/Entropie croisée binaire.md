#ml-1

# Définition

Pour un échantillon $i$ d'un problème de [[Classification binaire|classification binaire]], le modèle fournit la probabilité de la classe 1 :

$$\hat{y}_i = f(x_{i,1}, x_{i,2}) = \Pr(Y = 1 \mid X = x_i)$$

La probabilité que le modèle donne la bonne réponse sur cet échantillon s'écrit, avec $y_i \in \{0, 1\}$ :

$$\ell(\hat{y}_i, y_i) = \hat{y}_i^{y_i} \times (1 - \hat{y}_i)^{1 - y_i}$$

- si $y_i = 1$, seul le premier facteur subsiste, $\hat{y}_i$ ;
- si $y_i = 0$, seul le second subsiste, $1 - \hat{y}_i$.

Une seule formule couvre les deux cas, sans test conditionnel.

Les échantillons étant indépendants, la [[Fonction de vraisemblance|vraisemblance]] du jeu de données est le produit de ces probabilités :

$$\mathcal{L} = \prod_i \hat{y}_i^{y_i} (1 - \hat{y}_i)^{1 - y_i}$$

La [[Méthode du maximum de vraisemblance|méthode du maximum de vraisemblance]] choisit les paramètres sous lesquels les étiquettes observées sont les plus probables.

En passant au logarithme, la log-vraisemblance devient une somme :

$$LL = \ln \mathcal{L} = \sum_i \left[ y_i \ln \hat{y}_i + (1 - y_i) \ln(1 - \hat{y}_i) \right]$$

L'**entropie croisée binaire** est l'opposé de cette log-vraisemblance :

$$\mathrm{BCE} = -LL = -\sum_i \left[ y_i \ln \hat{y}_i + (1 - y_i) \ln(1 - \hat{y}_i) \right]$$

# Propriétés

Avec $\hat{y} = \sigma(z)$, le gradient de la perte par rapport au score $z$ dépend du choix de la perte.

Avec l'erreur quadratique $\ell = (\hat{y} - y)^2$ :

$$\frac{\partial \ell}{\partial z} = 2(\hat{y} - y) \sigma(z)(1 - \sigma(z))$$

Le facteur $\sigma(z)(1 - \sigma(z))$ tend vers 0 quand le modèle est confiant : un modèle confiant et faux n'a presque plus de gradient, et il reste bloqué exactement là où il se trompe le plus.

Avec l'entropie croisée binaire, le facteur $\sigma(z)(1 - \sigma(z))$ se compense :

$$\frac{\partial \ell}{\partial z} = \hat{y} - y$$

On retrouve la même forme qu'en [[Régression linéaire]] : le gradient vaut la prédiction moins la vérité. La perte n'est donc pas choisie pour son écriture, mais pour son gradient.

# Remarque

- Un produit de nombreux nombres inférieurs à 1 sous-déborde rapidement vers 0 ; le logarithme transforme ce produit en somme et évite ce sous-débordement.
- La fonction $\ln$ est croissante : la vraisemblance et la log-vraisemblance atteignent leur maximum aux mêmes valeurs des paramètres.
- En pratique, `torch.nn.BCELoss` calcule cette perte, et `torch.nn.BCEWithLogitsLoss` y intègre la sigmoïde, ce qui est numériquement plus sûr.

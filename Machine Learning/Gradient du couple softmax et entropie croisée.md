#ml-1

# Propriétés

Pour un échantillon, le réseau produit les probabilités $\hat{y} = \operatorname{softmax}(z)$ avec la [[Fonction softmax]], et la perte $\ell$ mesure l'[[Entropie croisée multi-classe|entropie croisée]] entre $\hat{y}$ et la vérité écrite en one-hot, $y = (0, \dots, 1, \dots, 0)$.

Le gradient de la perte par rapport aux scores $z$ vaut alors, composante par composante :

$$\frac{\partial \ell}{\partial z_c} = \hat{y}_c - y_c$$

soit, en notation vectorielle :

$$\nabla_z \ell = \hat{y} - y$$

Le gradient est donc **la prédiction moins la vérité**, de la même forme qu'en [[Régression linéaire|régression linéaire]] et qu'en [[Régression logistique|régression logistique]] : le couple softmax et entropie croisée ne fait pas exception à la règle.

# Interprétation

La composante $\hat{y}_c - y_c$ est l'erreur commise sur la classe $c$ :

- pour la classe correcte, $y_c = 1$ et la composante vaut $\hat{y}_c - 1$, négative : la [[Descente de gradient]] augmente le score de cette classe ;
- pour une classe fausse, $y_c = 0$ et la composante vaut $\hat{y}_c$, positive : la descente diminue son score.

Chaque classe est ainsi corrigée proportionnellement à son erreur : plus la probabilité prédite pour une classe fausse est forte, plus son score baisse.

# Exemple

Sur la photo du chat, le modèle renvoie $\hat{y} = (0.24, 0.66, 0.10)$ pour les trois classes chat, chien et oiseau, alors que la vérité one-hot est $y = (1, 0, 0)$. Le gradient vaut

$$\hat{y} - y = (0.24 - 1,\; 0.66,\; 0.10) = (-0.76,\; 0.66,\; 0.10)$$

La mise à jour qui en découle :

- pousse le score du chat vers le haut ;
- abaisse beaucoup le score du chien ;
- abaisse un peu le score de l'oiseau.

# Remarque

Garder l'erreur quadratique $\ell = (\hat{y} - y)^2$ avec $\hat{y} = \sigma(z)$, la sigmoïde de la [[Régression logistique]], aurait donné un tout autre gradient :

$$\frac{\partial \ell}{\partial z} = 2(\hat{y} - y)\,\sigma(z)\bigl(1 - \sigma(z)\bigr)$$

Le facteur $\sigma(z)(1 - \sigma(z))$ tend vers $0$ quand le modèle est confiant : confiant et faux, le gradient s'annule et le modèle reste bloqué exactement là où il est le plus mauvais. L'[[Entropie croisée binaire]] évite ce piège, le terme $\sigma'(z)$ se compense et il reste $\hat{y} - y$. La perte n'est pas choisie pour sa beauté, mais pour son gradient.

Vérification de santé, par un modèle non entraîné :

- il répond environ $1/K$ pour chaque classe ;
- la perte vaut alors $\approx \ln K$, soit $\ln 3 = 1.10$ pour trois classes ;
- le cas $K = 2$ donne $\ln 2 = 0.693$.

#ml-1

# Définition

La **normalisation par lots** (*batch normalization*) est une couche qui normalise chaque caractéristique à la volée, à l'intérieur du réseau.

- À l'entraînement, la moyenne et la variance utilisées sont celles du mini-lot courant.
- Au test, ce sont des moyennes courantes, accumulées pendant l'entraînement.
- Une échelle et un décalage appris s'appliquent ensuite.

Pour une caractéristique $x$ du mini-lot $\mathcal{B}$ :

$$\hat{x} = \frac{x - \mu_{\mathcal{B}}}{\sqrt{\sigma_{\mathcal{B}}^2 + \varepsilon}}$$

$$y = \gamma\, \hat{x} + \beta$$

où $\mu_{\mathcal{B}}$ et $\sigma_{\mathcal{B}}^2$ sont la moyenne et la variance du mini-lot, $\varepsilon$ une petite constante qui évite une division par zéro, et $\gamma$, $\beta$ l'échelle et le décalage appris.

# Interprétation

Le problème est le même qu'à l'entrée du réseau, mais à l'intérieur : les entrées d'une couche cachée dérivent à mesure que les poids changent.
Un [[Normalisation des entrées|normaliseur appliqué aux entrées]] ne peut pas y remédier : ces valeurs n'existent pas avant l'entraînement.
La couche recalcule donc ses statistiques sur chaque [[Lots, époques et chargement des données|mini-lot]] et normalise les caractéristiques au passage.

# Remarque

- La couche se comporte différemment à l'entraînement et au test : c'est la raison d'être de `model.train()` et `model.eval()` dans une [[Boucle d'entraînement et validation|boucle d'entraînement]].
- À l'entraînement, les statistiques sont recalculées sur le mini-lot courant ; au test, les moyennes courantes sont figées, aucune statistique n'est recalculée.

# Exemple

Dans un [[Perceptron multicouche]], la couche se place entre la couche linéaire et l'activation :

```python
nn.Sequential(
    nn.Linear(10, 100),
    nn.BatchNorm1d(100),
    nn.ReLU(),
    nn.Linear(100, 1),
)
```

Ici, la couche linéaire produit 100 caractéristiques, que `nn.BatchNorm1d(100)` normalise avant la non-linéarité.

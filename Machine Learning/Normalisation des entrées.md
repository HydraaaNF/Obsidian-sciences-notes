#ml-1

# Définition

La **normalisation des entrées** ramène chaque caractéristique à une moyenne nulle et à un écart-type de un, par la transformation

$$x' = (x - \mu)/\sigma$$

où $\mu$ et $\sigma$ sont la moyenne et l'écart-type de la caractéristique, estimés sur le jeu d'entraînement.

# Interprétation

- Les activations sont centrées sur 0, et plates loin de 0.
- De grandes valeurs d'entrée poussent $z = xa^\top + b$ loin de 0 : dans la région plate le gradient est minuscule, la convergence lente ou nulle, la sigmoïde sature à nouveau.
- Des caractéristiques à des échelles très différentes (un âge en années, un revenu en euros) ne peuvent pas partager un taux d'apprentissage adapté à tous les poids.

# Algorithme

- Estimer $\mu$ et $\sigma$ sur le jeu d'entraînement seulement.
- Transformer le jeu d'entraînement avec ces valeurs.
- Appliquer la même transformation, avec les mêmes $\mu$ et $\sigma$, à tous les autres jeux.

# Exemple

**Statistiques estimées sur l'entraînement (PyTorch)**

```python
mu, sigma = x_train.mean(dim=0), x_train.std(dim=0)
x_train = (x_train - mu) / sigma
x_test = (x_test - mu) / sigma    # mêmes mu et sigma
```

**Avec scikit-learn**

- `StandardScaler` : moyenne 0, écart-type 1.
- `MinMaxScaler` : dans $[0, 1]$, ou un autre intervalle ($[-1, 1]$).
- Une interface unique :
  - `fit` : estime les paramètres ($\mu$ et $\sigma$, ou le minimum et le maximum) ;
  - `transform` : les applique ;
  - `inverse_transform` : revient aux unités d'origine, par exemple pour lire une prédiction.

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler().fit(x_train)    # entraînement seulement
x_train = scaler.transform(x_train)
x_test = scaler.transform(x_test)         # mêmes mu et sigma
```

# Remarque

- $\mu$ et $\sigma$ se calculent sur le [[Jeux d'entraînement, de développement et de test|jeu d'entraînement]] uniquement, puis s'appliquent à tous les jeux : les estimer sur l'ensemble des données ferait fuiter le jeu de test dans l'entraînement.
- Les mêmes valeurs servent pour chaque [[Lots, époques et chargement des données|lot]].
- La [[Normalisation par lots]] normalise les activations à l'intérieur du réseau, sur chaque mini-lot, et non les entrées une fois pour toutes.

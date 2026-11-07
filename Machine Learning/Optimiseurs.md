#ml-1

# Définition

Un **optimiseur** est l'objet qui applique la règle de mise à jour aux paramètres d'un modèle, à partir des gradients calculés. Pour la [[Descente de gradient]], la règle s'écrit, avec $\boldsymbol{g} = \nabla L(\theta)$ le gradient de la perte :

$$\theta \leftarrow \theta - \alpha\, \boldsymbol{g}$$

où $\alpha$ est le taux d'apprentissage et $\theta$ l'ensemble des paramètres du modèle.

# Propriétés

Les variantes usuelles gardent la boucle d'entraînement et ne changent que la règle de mise à jour.

**SGD** applique la règle de la [[Descente de gradient]] telle quelle.

**Momentum** suit une somme courante des gradients passés :

$$\boldsymbol{v} \leftarrow \beta \boldsymbol{v} + \boldsymbol{g}$$

$$\theta \leftarrow \theta - \alpha\, \boldsymbol{v}$$

**Adam** ajoute au momentum une taille de pas propre à chaque paramètre :

$$\boldsymbol{m} \leftarrow \beta_1 \boldsymbol{m} + (1 - \beta_1)\, \boldsymbol{g}$$

$$\boldsymbol{s} \leftarrow \beta_2 \boldsymbol{s} + (1 - \beta_2)\, \boldsymbol{g}^2$$

$$\theta \leftarrow \theta - \alpha\, \frac{\boldsymbol{m}}{\sqrt{\boldsymbol{s}} + \varepsilon}$$

Les grandeurs $\boldsymbol{m}$ et $\boldsymbol{s}$ sont des moyennes exponentielles du gradient et de son carré, et une correction de ces deux grandeurs s'applique sur les premiers pas.

Adam fonctionne bien avec son taux d'apprentissage par défaut $\alpha = 10^{-3}$.

En PyTorch, la variante se choisit à la construction de l'optimiseur :

```python
optim.SGD(model.parameters(), lr=0.1, momentum=0.9)
optim.Adam(model.parameters(), lr=1e-3)
```

# Algorithme

L'optimiseur reçoit les paramètres du modèle ; `step()` les met tous à jour, `zero_grad()` remet leurs gradients à zéro avant le calcul suivant.

```python
optimizer = torch.optim.SGD([a, b], lr=0.1)

for step in range(n_steps):
    optimizer.zero_grad()          # a.grad.zero_(), ...
    loss = ((model(a, b, x) - y) ** 2).mean()
    loss.backward()
    optimizer.step()               # a -= lr * a.grad, ...
```

Ce sont les mêmes quatre lignes, `zero_grad()`, le calcul de la perte, `backward()` puis `step()`, pour tout modèle : seule la règle de mise à jour change. La version écrite à la main, sans classes, se trouve dans [[Entraîner un modèle linéaire pas à pas]] ; c'est `backward()` qui remplit les gradients, voir [[Rétropropagation]].

# Exemple

Un modèle, une fonction de perte et un optimiseur remplacent chacun une ligne écrite à la main :

```python
model = MLP(2, 8, 1)
loss_fn = nn.BCEWithLogitsLoss()   # binary cross-entropy
optimizer = torch.optim.SGD(model.parameters(), lr=0.1)

for epoch in range(n_epochs):
    optimizer.zero_grad()          # a.grad.zero_()
    loss = loss_fn(model(x), y)    # forward
    loss.backward()                # gradients
    optimizer.step()               # a -= lr * a.grad
```

Les pertes correspondantes sont `nn.MSELoss` en régression, `nn.BCELoss` ou `nn.BCEWithLogitsLoss` en classification binaire, voir [[Entropie croisée binaire]].

Avec `BCEWithLogitsLoss`, aucune sigmoïde dans le modèle : on prédit la classe 1 quand la sortie est $\geq 0$.

# Remarque

Le momentum et Adam généralisent la [[Descente de gradient]] : la règle de base reste le point de départ, la mémoire des gradients passés et la taille de pas par paramètre s'y ajoutent.

Le taux d'apprentissage $\alpha$ n'est pas forcément constant pendant l'entraînement, voir [[Planificateurs de taux d'apprentissage]] ; la boucle complète, avec époques et validation, est décrite dans [[Boucle d'entraînement et validation]].

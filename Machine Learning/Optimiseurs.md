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

Les pertes usuelles sont `nn.MSELoss` en régression, `nn.BCELoss` ou `nn.BCEWithLogitsLoss` en classification binaire, voir [[Entropie croisée binaire]]. La boucle complète est décrite dans [[Boucle d'entraînement et validation]].

Avec `BCEWithLogitsLoss`, aucune sigmoïde dans le modèle : on prédit la classe 1 quand la sortie est $\geq 0$.

# Interprétation

Chaque grandeur d'Adam a la forme des paramètres : $\boldsymbol{m}$ et $\boldsymbol{s}$ comptent une composante par paramètre, et toutes les opérations sont terme à terme. Adam stocke donc deux copies du modèle en plus des gradients.

La mise à jour se lit en deux temps. Le numérateur $\boldsymbol{m}$ est l'élan, une moyenne des gradients passés où le gradient d'il y a un pas pèse $\beta_1$ fois celui d'aujourd'hui, celui d'il y a deux pas $\beta_1^2$, et ainsi de suite :

$$\boldsymbol{m}_t = (1-\beta_1)\sum_{k=1}^{t}\beta_1^{\,t-k}\,\boldsymbol{g}_k$$

Ces poids décroissent géométriquement, d'où le nom de moyenne exponentielle, et leur somme vaut $1-\beta_1^t$ : la correction de biais divise par ce facteur, ce qui compte sur les premiers pas où $\boldsymbol{m}$ part de zéro. Avec $\beta_1 = 0{,}9$, l'âge moyen des gradients retenus vaut neuf pas.

Le dénominateur $\sqrt{\boldsymbol{s}}$ est une échelle : $\boldsymbol{s}$ moyenne les carrés des gradients, donc $\sqrt{\boldsymbol{s}}$ est de l'ordre du gradient typique de cette coordonnée. Diviser par lui rend le pas indépendant de l'échelle, alors que la même multiplication de la perte fait osciller SGD. Le $\varepsilon$ évite seulement une division par zéro sur une coordonnée dont le gradient est resté nul.

Face à SGD, le gain tient en trois points :

- un pas propre à chaque coordonnée, donc pas de réglage de $\alpha$ par groupe de paramètres ;
- l'invariance d'échelle, qui rend le taux par défaut $10^{-3}$ utilisable tel quel ;
- une mémoire courte des gradients, qui lisse le bruit des mini-lots.

Le revers est réel : deux copies du modèle en mémoire, une généralisation pas toujours meilleure, d'où AdamW et le weight decay découplé, et un pas borné à environ $\alpha$ par coordonnée, qui limite la précision finale.

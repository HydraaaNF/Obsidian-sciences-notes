#ml-1

# Algorithme

Une boucle d'entraînement s'écrit avec les classes de PyTorch : chacune remplace une ligne que l'on écrivait à la main sur un tenseur.

```python
model = MLP(2, 8, 1)
loss_fn = nn.BCEWithLogitsLoss()   # TP2: by hand
optimizer = torch.optim.SGD(model.parameters(), lr=0.1)

for epoch in range(n_epochs):
    optimizer.zero_grad()          # TP1: a.grad.zero_()
    loss = loss_fn(model(x), y)    # forward
    loss.backward()                # as in TP1
    optimizer.step()               # TP1: a -= lr * a.grad
```

Correspondance avec la version écrite à la main :

- `optimizer.zero_grad()` remet à zéro le gradient des paramètres, à la place de `a.grad.zero_()` ;
- `loss_fn(model(x), y)` calcule la passe avant et la perte en une seule expression ;
- `loss.backward()` remplit les gradients par [[Rétropropagation]], sur le [[Graphe de calcul]] construit par la [[Différenciation automatique]] ;
- `optimizer.step()` applique la mise à jour des paramètres, celle de la [[Descente de gradient]] que les [[Optimiseurs]] généralisent.

Le modèle `MLP(2, 8, 1)` a deux entrées, huit unités cachées et une sortie ; il se construit comme dans [[Composer un réseau avec PyTorch]] et s'entraîne sur des mini-lots fournis par [[Lots, époques et chargement des données|les lots et le chargement des données]].

Après chaque époque, la même boucle mesure la perte sur le jeu de validation :

```python
model.eval()
with torch.no_grad():
    valid_loss = loss_fn(model(x_valid), y_valid)
model.train()
```

# Remarque

- Le choix de la perte suit la tâche : `nn.MSELoss` pour une régression, `nn.BCELoss` ou `nn.BCEWithLogitsLoss` pour une [[Classification binaire]].
- Avec `nn.BCEWithLogitsLoss`, la sigmoïde est intégrée à la perte : le modèle doit donc sortir un logit, sans sigmoïde dans le réseau, et la classe 1 est prédite dès que la sortie est $\geq 0$, ce qui correspond au [[Seuil de décision|seuil]] $0{,}5$ sur la probabilité.
- La validation ne met à jour aucun paramètre, donc aucun graphe n'a besoin d'être enregistré : `torch.no_grad()` rend le calcul plus rapide et plus léger en mémoire.
- Certaines couches se comportent différemment à l'entraînement et à l'évaluation (dropout, batch normalization) : `model.eval()` avant d'évaluer, `model.train()` après.
- Une perte d'entraînement qui descend pendant que la perte de validation remonte signale un [[Surapprentissage et sous-apprentissage|surapprentissage]].
- Le jeu de validation est celui du protocole de découpage décrit dans [[Jeux d'entraînement, de développement et de test]] ; il ne se confond ni avec le jeu d'entraînement ni avec le jeu de test.
- Ce qui a été appris se conserve avec `model.state_dict()`, voir [[Sauvegarde et reprise de l'entraînement]].

#ml-1

# Définition

`nn.CrossEntropyLoss` prend en entrée les **scores** produits par le modèle, et non des probabilités : la [[Fonction softmax|fonction softmax]] est intégrée à la perte. C'est la même logique que `BCEWithLogitsLoss` pour l'[[Entropie croisée binaire|entropie croisée binaire]], et pour la même raison : le logarithme d'un softmax se calcule de façon stable. La même perte s'écrit aussi comme `nn.LogSoftmax` suivi de `nn.NLLLoss`.

Conséquence : le modèle ne doit pas se terminer par un softmax.

La cible ne contient pas de probabilités mais les **indices** de classe : des entiers de type `long`, de forme $(B,)$ pour un lot de taille $B$, ni encodage one-hot ni forme $(B, 1)$.

# Exemple

```python
model = nn.Sequential(nn.Linear(4, 16), nn.ReLU(),
                      nn.Linear(16, 3))  # 3 scores
loss_fn = nn.CrossEntropyLoss()

z = torch.tensor([[1.0, 2.0, 0.1]])      # cat, dog, bird
y = torch.tensor([0])                    # a cat: index 0
loss_fn(z, y)                            # 1.417, by hand

y_pred = z.argmax(dim=1)                 # tensor([1]): dog
proba = torch.softmax(z, dim=1)          # if you need them
```

Le modèle produit trois scores, un par classe (chat, chien, oiseau), pour un lot d'un seul échantillon ; la cible est l'indice $0$, la classe chat. La perte vaut $1.417$, soit $-\ln(0.2424)$ : $0.2424$ est la probabilité affectée à la classe $0$ par le softmax des scores.

`argmax` appliqué aux scores, sans passer par les probabilités, donne la classe prédite $1$ (chien) ; les probabilités ne sont calculées à part avec `torch.softmax` que lorsqu'on en a besoin.

# Remarque

- En [[Classification multi-étiquette|classification multi-étiquette]], plusieurs classes peuvent être vraies à la fois : la perte devient `BCEWithLogitsLoss`, la cible est un flottant de forme $(B, K)$ et chaque classe se décide par $z > 0$ sur son score.
- La perte elle-même est définie dans [[Entropie croisée multi-classe]].
- L'appel de cette perte s'inscrit dans la [[Boucle d'entraînement et validation]].

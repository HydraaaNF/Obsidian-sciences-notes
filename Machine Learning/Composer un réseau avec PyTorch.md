#ml-1

# Définition

Un réseau PyTorch s'assemble à partir de modules : chaque module transforme son entrée en sortie et peut contenir des paramètres. Trois briques suffisent à le composer.

Une couche linéaire `nn.Linear(n, m)` est un module porteur de paramètres, qui calcule

$$xA^\top + b$$

avec $A$ de taille $m \times n$ et $b$ de $m$ valeurs. C'est le produit matriciel de la [[Forme matricielle de la régression|forme matricielle de la régression]], celui qu'une couche de [[Perceptron multicouche]] écrit à la main. La matrice $A$ et le vecteur $b$ sont créés à l'initialisation, gradients activés.

Une activation est un module sans paramètre : `nn.Sigmoid()`, `nn.Tanh()` ou `nn.ReLU()`, à choisir parmi les [[Fonctions d'activation]].

Le chaînage se fait avec `nn.Sequential` : la sortie de chaque module devient l'entrée du suivant, et les tailles doivent correspondre d'une couche à l'autre. Un réseau personnalisé se définit plutôt en sous-classant `nn.Module` : les couches sont des attributs, le calcul est écrit dans `forward`.

# Propriétés

- La dimension de lot vient en premier : `nn.Linear(n, m)` transforme un lot de forme $(B, n)$ en un lot de forme $(B, m)$.
- La sortie d'une couche linéaire à une seule unité est de forme $(B, 1)$, et non $(B,)$ : la cible doit recevoir la même forme.
- Pour `nn.Linear(3, 1)`, `weight` est de forme $(1, 3)$ et `bias` de forme $(1,)$ : une ligne de poids par unité de sortie, un biais par unité.
- Un module est appelable : `mlp(x)` exécute la chaîne des couches.
- `model(x)` appelle `forward(x)`, et `model.parameters()` parcourt tous les poids du modèle, ce qui les rend disponibles pour la [[Différenciation automatique]] et pour l'optimiseur de la [[Boucle d'entraînement et validation]].

# Exemple

Une couche linéaire de trois entrées vers une sortie, suivie d'une sigmoïde, reproduit une régression logistique :

```python
layer = nn.Linear(3, 1)          # TP2: a (3 weights) and b
layer.weight.shape               # torch.Size([1, 3])
layer.bias.shape                 # torch.Size([1])

x = torch.randn(16, 3)          # 16 samples
layer(x).shape                   # torch.Size([16, 1])
nn.Sigmoid()(layer(x))         # logistic regression
```

Le même empilement par `nn.Sequential` donne la régression logistique puis le réseau du [[Problème du ou exclusif|XOR]] :

```python
logistic = nn.Sequential(nn.Linear(2, 1), nn.Sigmoid())

mlp = nn.Sequential(
    nn.Linear(2, 2), nn.Tanh(),     # hidden layer, 2 -> 2
    nn.Linear(2, 1),                # output layer, 2 -> 1
)
y_pred = mlp(x)                     # (B, 2) -> (B, 1)
```

La version en classe garde les couches et leurs paramètres dans un même objet :

```python
class MLP(nn.Module):
    def __init__(self, n, h, m):
        super().__init__()
        self.hidden = nn.Linear(n, h)
        self.output = nn.Linear(h, m)

    def forward(self, x):
        h = torch.tanh(self.hidden(x))
        return self.output(h)

model = MLP(2, 2, 1)
y_pred = model(x)                     # calls forward
```

# Remarque

Écrire le modèle comme une fonction `model(a, b, x)` qui reçoit les poids en arguments, avec `a` et `b` promenés séparément, disperse les paramètres dans le code appelant. Un module les garde ensemble : `model.parameters()` les énumère sans qu'on ait à les nommer un par un.

Le réseau du XOR tient en trois lignes : deux entrées, deux neurones cachés avec une tangente hyperbolique, une sortie. Sans activation entre les couches linéaires, l'empilement se réduit à une seule transformation affine, voir [[Composition de couches linéaires]].

Le nombre d'entrées $n$ de la première couche, le nombre $h$ d'unités cachées et le nombre $m$ de sorties sont fixés à la construction : ce sont des [[Hyper-paramètres]], pas des poids appris.

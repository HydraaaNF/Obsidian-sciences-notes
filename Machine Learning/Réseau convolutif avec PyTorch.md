#ml-2

# Modèle

Un réseau convolutif pour images de 32 x 32 pixels en trois canaux se compose comme une chaîne `nn.Sequential` : la sortie de chaque module devient l'entrée du suivant, ce qui applique [[Composer un réseau avec PyTorch]] à un [[Réseau de neurones convolutif]].

Chaque étape est un module :

- `nn.Conv2d(3, 16, kernel_size=3, padding=1)` : [[Couche de convolution]] de 3 canaux d'entrée vers 16 canaux de sortie, noyau 3 x 3, marge d'un pixel sur les bords.
- `nn.ReLU()` : activation sans paramètre, voir [[Fonctions d'activation]].
- `nn.MaxPool2d(2)` : [[Max pooling]] de fenêtre 2 x 2, qui divise hauteur et largeur par deux.
- `nn.Conv2d(16, 32, kernel_size=3, padding=1)` : seconde convolution, de 16 vers 32 canaux, même noyau et même marge.
- `nn.ReLU()`.
- `nn.MaxPool2d(2)`.
- `nn.Flatten()` : mise à plat de la carte de caractéristiques en un vecteur.
- `nn.Dropout(0.5)` : neutralisation aléatoire de la moitié des valeurs, voir [[Dropout]].
- `nn.Linear(32 * 8 * 8, 10)` : couche dense de 2048 entrées vers 10 sorties, une par classe.

# Algorithme

```python
model = nn.Sequential(
    nn.Conv2d(3, 16, kernel_size=3, padding=1),   # -> 16 x 32 x 32
    nn.ReLU(),
    nn.MaxPool2d(2),                              # -> 16 x 16 x 16
    nn.Conv2d(16, 32, kernel_size=3, padding=1),  # -> 32 x 16 x 16
    nn.ReLU(),
    nn.MaxPool2d(2),                              # -> 32 x 8 x 8
    nn.Flatten(),                                 # -> 2048
    nn.Dropout(0.5),                              # training only
    nn.Linear(32 * 8 * 8, 10),                    # -> 10 classes
)

x = torch.randn(64, 3, 32, 32)   # batch of 64 RGB images
print(model(x).shape)            # -> torch.Size([64, 10])
```

Le comportement du dropout suit le mode du modèle :

```python
model.train()   # Dropout active
model.eval()    # Dropout inactive
```

# Propriétés

Avec un noyau de taille $k$, une marge $p$ et un pas de 1, une convolution transforme une dimension spatiale $n$ en $n_{\text{out}} = n + 2p - k + 1$, voir [[Taille de sortie d'une convolution]] ; ici $32 + 2 - 3 + 1 = 32$ pour la première convolution, puis $16 + 2 - 3 + 1 = 16$ pour la seconde, dont l'entrée est déjà ramenée à 16 par le premier pooling ; chaque sous-échantillonnage divise ensuite hauteur et largeur par deux.

Dimensions d'un lot de 64 images à chaque étape :

- entrée : $(64, 3, 32, 32)$
- première convolution : $(64, 16, 32, 32)$
- premier max pooling : $(64, 16, 16, 16)$
- seconde convolution : $(64, 32, 16, 16)$
- second max pooling : $(64, 32, 8, 8)$
- mise à plat : $(64, 2048)$, car $32 \times 8 \times 8 = 2048$
- couche dense : $(64, 10)$

# Interprétation

- Les convolutions augmentent le nombre de canaux, de 3 à 16 puis 32, tandis que le pooling réduit la résolution spatiale, de 32 à 16 puis 8 : le réseau décrit des motifs de plus en plus abstraits sur une grille de plus en plus grossière.
- La marge d'un pixel compense le noyau 3 x 3 : sans elle, chaque convolution rognerait de deux pixels la carte et l'information des bords se perdrait plus vite.
- La mise à plat fournit les 2048 valeurs que la couche dense combine en 10 scores de classe : c'est la charnière entre la partie convolutive et la tête de classification.
- Le dropout ne sert qu'à l'entraînement ; en évaluation, il laisse passer toutes les valeurs.

# Remarque

- Les commentaires de forme oublient la dimension de lot : la sortie de la seconde convolution s'écrit 32 x 16 x 16, soit 32 canaux de 16 x 16, et non 32 x 32 x 16, où la hauteur reste à 32 alors que le pooling l'a ramenée à 16. Le tenseur complet reste $(64, 32, 16, 16)$, voir [[Forme d'un tenseur]] et [[Tenseurs PyTorch]].
- `model.train()` active le dropout, `model.eval()` le désactive ; oublier le second mode fausse l'évaluation.
- L'ordre des dimensions est celui de PyTorch, lot puis canaux puis hauteur puis largeur, ce qui explique `torch.randn(64, 3, 32, 32)` pour un lot d'images en trois couleurs.

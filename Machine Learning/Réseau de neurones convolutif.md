#ml-2

# Définition

Un réseau de neurones convolutif est un [[Réseau de neurones]] dont les couches combinent une [[Couche de convolution|convolution]] et une non-linéarité, puis une opération de pooling ; ce motif est répété plusieurs fois. Les cartes de caractéristiques obtenues sont ensuite aplaties, puis traitées par un classifieur fait de [[Perceptron multicouche|couches denses]].

# Algorithme

```
pour chaque bloc convolutif :
    cartes = convolution(cartes)
    cartes = activation(cartes)      # par exemple ReLU
    cartes = pooling(cartes)         # par exemple max pooling
vecteur = aplatir(cartes)
sortie  = couches_denses(vecteur)    # classifieur
```

# Interprétation

Chaque bloc extrait des motifs d'un niveau d'abstraction supérieur au précédent. Plus une couche est profonde, plus la représentation qu'elle porte est chargée de sens :

- les premières couches détectent des bords ;
- les couches intermédiaires détectent des textures ;
- les couches profondes détectent des parties d'objet.

# Exemple

Classification d'images en 10 classes à partir d'images de taille $3 \times 32 \times 32$ (3 canaux de couleur, 32 pixels de côté) :

| Étape | Taille de sortie |
|---|---|
| image d'entrée | $3 \times 32 \times 32$ |
| convolution $3 \times 3$ et ReLU, 16 canaux | $16 \times 32 \times 32$ |
| max pooling | $16 \times 16 \times 16$ |
| convolution $3 \times 3$ et ReLU, 32 canaux | $32 \times 16 \times 16$ |
| max pooling | $32 \times 8 \times 8$ |
| aplatissement puis couches denses | 10 classes |

Le plateau d'un jeu de Go, de taille $19 \times 19$, se traite de la même façon comme une image à 48 canaux (pierres, libertés, et autres descripteurs de la position). Deux réseaux convolutifs y sont appliqués :

- un réseau de politique, qui choisit le coup suivant par classification sur les 361 intersections du plateau ;
- un réseau de valeur, qui estime l'issue de la partie.

La recherche arborescente et l'apprentissage par auto-jeu qui complètent un tel système relèvent d'autres méthodes.

# Remarque

Les architectures de réseaux convolutifs les plus connues sont LeNet, AlexNet et ResNet ; cette dernière ajoute des [[Connexions résiduelles]] pour faciliter l'entraînement de réseaux très profonds.

L'assemblage concret d'un tel réseau avec `nn.Sequential` est détaillé dans [[Réseau convolutif avec PyTorch]], qui applique la démarche de [[Composer un réseau avec PyTorch]] en intercalant [[Couche de convolution|convolutions]] et [[Max pooling]].

Le mécanisme d'[[Attention dans un réseau convolutif|attention]] peut être ajouté à un tel réseau pour pondérer les pixels ou les canaux avant la classification.

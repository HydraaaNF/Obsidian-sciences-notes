#ml-1

# Définition

L'indexation d'un [[Tenseurs PyTorch|tenseur PyTorch]] suit la même convention que celle des [[Tableaux NumPy et pandas|tableaux NumPy]] :

- une liste d'indices sélectionne et réordonne les éléments ;
- un masque booléen filtre les éléments.

Une réduction prend un argument `dim` : c'est l'axe qui disparaît du résultat. Avec `dim=0`, la réduction parcourt les échantillons et produit une valeur par caractéristique.

# Exemple

```python
x = torch.tensor([[1., 2., 3.],
                 [4., 5., 6.]])   # (2, 3)
x[:, 0:2]                         # the first two columns
x[:, [2, 0, 1]]                  # columns reordered
x[x > 2]                          # tensor([3., 4., 5., 6.])

x.mean(dim=0)                     # tensor([2.5, 3.5, 4.5])
x.sum(dim=1)                      # tensor([ 6., 15.])
x.argmax(dim=1)                  # tensor([2, 2])
x.mean(dim=0, keepdim=True).shape   # (1, 3), not (3,)
```

La moyenne sur `dim=0` agrège les deux lignes et renvoie une valeur par colonne, donc une valeur par caractéristique. La somme sur `dim=1` agrège les colonnes de chaque ligne et renvoie une valeur par échantillon.

# Remarque

`keepdim=True` conserve l'axe réduit avec une taille de 1 : la moyenne sur `dim=0` d'un tenseur de [[Forme d'un tenseur|forme]] `(2, 3)` donne un résultat de forme `(1, 3)` au lieu de `(3,)`. L'axe conservé permet ensuite de combiner le résultat avec le tenseur d'origine par [[Diffusion entre tenseurs|diffusion]].

L'indexation et les réductions relèvent des [[Opérations sur les tenseurs]] : elles s'appliquent d'un bloc à tout le tenseur.

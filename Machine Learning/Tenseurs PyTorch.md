#ml-1

# Définition

PyTorch est une bibliothèque de calcul sur les [[Tenseur|tenseurs]], très proche de NumPy (voir [[Tableaux NumPy et pandas]]). Ses tenseurs se distinguent par deux capacités :

- contrôler où vit la mémoire, sur CPU ou sur GPU (`cuda`), grâce à l'attribut `device` ;
- fournir la [[Différenciation automatique]] nécessaire à l'entraînement.

Sur CPU, un tenseur peut partager sa mémoire avec un `numpy.ndarray`.

# Interprétation

La différenciation automatique est la raison d'être de PyTorch. Le choix de l'appareil de calcul (voir [[Calcul sur GPU]]) et le partage de mémoire avec NumPy sont des commodités ; c'est l'autodiff qui motive le recours à la bibliothèque.

# Exemple

Création directe de tenseurs :

```python
torch.tensor([[1., 2.], [3., 4.]])    # from Python lists
torch.zeros(3, 2), torch.ones(3, 2)   # filled
torch.arange(0, 10, 2)               # tensor([0, 2, 4, 6, 8])
torch.linspace(0, 1, 5)              # 5 values, from 0 to 1
torch.rand(3, 2)                     # uniform in [0, 1)
torch.randn(3, 2)                    # standard normal
```

D'un fichier CSV aux tenseurs, avec les entrées `weight` et `age` et la sortie `height` :

```python
df = pd.read_csv("population.csv")

x = torch.tensor(df[["weight", "age"]].to_numpy(),
                 dtype=torch.float32)   # (N, 2)
y = torch.tensor(df[["height"]].to_numpy(),
                 dtype=torch.float32)   # (N, 1)
```

# Remarque

Le `dtype` est deviné à partir des valeurs :

- `torch.tensor([1., 2.])` : `float32`, le type par défaut pour les réels ;
- `torch.tensor([1, 2])` : `int64`, mais les gradients exigent des flottants ;
- depuis NumPy : `float64`, qui entre en conflit avec des paramètres `float32`.

En cas de doute, le déclarer : `dtype=torch.float32`. Un tenseur d'entiers ne peut pas porter de gradient :

```python
torch.tensor([1, 2], requires_grad=True)
# RuntimeError: Only Tensors of floating point and
# complex dtype can require gradients
```

Une liste de colonnes, `df[["height"]]`, garde une table de forme $(N, 1)$, une colonne par sortie, comme la prédiction d'un modèle ; une colonne seule, `df["height"]`, donne un vecteur de forme $(N,)$.

Sans `dtype=torch.float32`, le `float64` de NumPy est conservé et le premier produit avec un paramètre échoue :

```
RuntimeError: mat1 and mat2 must have the same dtype,
but got Double and Float
```

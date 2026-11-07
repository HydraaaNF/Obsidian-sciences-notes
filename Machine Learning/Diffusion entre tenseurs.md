#ml-1

# Définition

La **diffusion** (broadcasting) est la règle qui rend compatibles les [[Forme d'un tenseur|formes]] de deux tenseurs engagés dans une [[Opérations sur les tenseurs|opération élément par élément]] :

- les deux formes sont alignées par la droite, dimension par dimension ;
- un axe de taille 1, ou un axe absent, est répété autant de fois qu'il le faut pour rejoindre la taille de l'autre tenseur.

# Exemple

Centrer chaque colonne d'une matrice, ou ajouter un biais à chaque ligne, tient en une ligne de code :

```python
x = torch.rand(5, 3)
(x - x.mean(dim=0)).shape    # (5, 3) - (3,) -> (5, 3)
```

Le vecteur des moyennes de colonnes a la forme $(3,)$ ; il est diffusé sur les cinq lignes de la matrice, qui garde la forme $(5, 3)$.

# Remarque

La diffusion est trompeuse quand une dimension manque d'un côté seulement : une colonne moins un vecteur donne une matrice, sans lever la moindre erreur.

```python
y_hat = torch.rand(5, 1)     # a model's prediction
y = torch.rand(5)            # a DataFrame column
(y_hat - y).shape           # torch.Size([5, 5]) !
```

Les formes $(5, 1)$ et $(5,)$ s'alignent par la droite : l'axe de taille 1 de la colonne est répété cinq fois, et l'axe absent du vecteur aussi, si bien que chaque prédiction se retrouve comparée à chaque cible. Une perte écrite à la main est alors silencieusement fausse, ce qui pèse sur l'évaluation d'un [[Lots, époques et chargement des données|lot]] entier.

Le réflexe est de vérifier les formes juste avant le calcul de la perte :

```python
assert y_hat.shape == y.shape, "fix the shapes first"
```

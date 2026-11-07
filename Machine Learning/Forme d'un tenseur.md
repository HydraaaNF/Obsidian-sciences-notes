#ml-1

# Définition

La **forme** d'un tenseur est la suite des tailles de ses axes, dans l'ordre des axes. Chaque nombre de la suite donne le nombre d'éléments le long d'un axe :

- forme `(4,)` : un seul axe, de 4 éléments ;
- forme `(1, 4)` : deux axes, une ligne de 4 éléments ;
- forme `(4, 1)` : deux axes, une colonne de 4 éléments.

Une même suite de valeurs peut donc s'écrire sous plusieurs formes, et le nombre de crochets à l'affichage donne le nombre d'axes.

# Exemple

Avec `v = torch.arange(4.)`, les mêmes quatre valeurs prennent trois formes :

- `v` s'écrit `[0, 1, 2, 3]` et a pour forme `(4,)` : un axe ;
- `v.unsqueeze(0)` s'écrit `[[0, 1, 2, 3]]` et a pour forme `(1, 4)` : une ligne ;
- `v.unsqueeze(1)` s'écrit `[[0], [1], [2], [3]]` et a pour forme `(4, 1)` : une colonne.

# Propriétés

Les formes se changent avec les opérations suivantes, qui ne modifient pas les valeurs :

- `unsqueeze(d)` ajoute un axe de taille 1 en position `d` ;
- `squeeze(d)` supprime cet axe ;
- `reshape` réorganise les valeurs dans une nouvelle forme, `-1` signifiant « le reste » ;
- `permute` échange des axes, comme la transposée `m.T` ;
- `torch.cat` empile des tenseurs le long d'un axe choisi.

```python
v.unsqueeze(1).squeeze(1)  # retour à (4,)
v.reshape(2, 2)            # (2, 2), mêmes valeurs
v.reshape(-1, 1)           # (4, 1) ; -1 : « le reste »
m.permute(1, 0)            # échange les axes, comme m.T

a, b = torch.ones(4, 1), torch.zeros(4, 1)
torch.cat((a, b), dim=1)   # (4, 2) : côte à côte
torch.cat((a, b), dim=0)   # (8, 1) : l'un sous l'autre
```

La concaténation s'arrête sur l'axe choisi : avec deux colonnes `(4, 1)`, `dim=1` les place côte à côte en `(4, 2)` et `dim=0` les empile en `(8, 1)`.

# Remarque

Changer la forme ne change ni les valeurs ni leur ordre de lecture : `(4,)`, `(1, 4)` et `(4, 1)` contiennent les mêmes quatre nombres. La distinction compte pour la suite du calcul, car les opérations entre tenseurs et la [[Diffusion entre tenseurs|diffusion]] raisonnent sur les axes, pas sur les valeurs.

Les tenseurs manipulés ici sont ceux de [[Tenseurs PyTorch]] ; leur forme est celle du [[Tenseur]] correspondant, et elle doit être vérifiée avant de passer les données à un modèle tel que le [[Perceptron multicouche]].

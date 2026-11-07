#ml-1

# Définition

Un **planificateur de taux d'apprentissage** fait varier le taux d'apprentissage au fil de l'entraînement : de grands pas d'abord, des pas plus petits à l'approche de l'optimum.

On note $\alpha_e$ le taux d'apprentissage à l'époque $e$. Le planificateur est branché sur l'[[Optimiseurs|optimiseur]] et fixe ce taux ; la règle de mise à jour de la [[Descente de gradient]] reste inchangée.

# Propriétés

PyTorch fournit les planificateurs dans `torch.optim.lr_scheduler`, chacun selon sa propre loi de variation :

- `StepLR` : $\alpha$ est multiplié par $\gamma$ toutes les $k$ époques
- `ExponentialLR` : $\alpha_{e+1} = \gamma\, \alpha_e$
- `MultiplicativeLR` : $\alpha_{e+1} = f(e)\, \alpha_e$
- `LambdaLR` : $\alpha_e = f(e)\, \alpha_0$

Dans les deux dernières, $f$ est une fonction de l'époque choisie par l'utilisateur.

# Exemple

Un planificateur exponentiel de facteur $0.9$, appelé une fois par époque :

```python
from torch.optim.lr_scheduler import ExponentialLR

scheduler = ExponentialLR(optimizer, gamma=0.9)
for epoch in range(n_epochs):
    for x_batch, y_batch in loader:
        ...                       # the four lines
    scheduler.step()              # once per epoch, after them
```

# Remarque

`scheduler.step()` s'appelle une fois par époque, après les quatre lignes de la boucle d'entraînement (voir [[Boucle d'entraînement et validation]]).

Le taux d'apprentissage ainsi planifié est celui que reçoit l'[[Optimiseurs|optimiseur]] à chaque mise à jour.

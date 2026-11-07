#ml-1

# Exemple

Tracer des données avec `matplotlib.pyplot` :

- données 1D : `plt.plot(values)` ;
- données 2D : `plt.plot(x, y)` pour des lignes, `plt.scatter(x, y)` pour des points ;
- puis libellés, limites et légende, et `plt.show()`.

```python
import matplotlib.pyplot as plt

plt.plot([2, 3, 4], [1, 3, 4], "o-", label="line")
plt.scatter([1, 4, 5], [1, 2, 1], label="points")
plt.xlabel("size")
plt.ylabel("darkness")
plt.xlim(0, 6)
plt.ylim(0, 5)
plt.legend()
plt.show()
```

Les valeurs tracées sont des séquences : listes Python ou [[Tableaux NumPy et pandas|tableaux NumPy]].

# Remarque

Un [[Tenseur|tenseur]] porteur de gradient doit d'abord être détaché avant le tracé : `y_pred.detach()`.

Ce détachement concerne les [[Tenseurs PyTorch|tenseurs PyTorch]] construits par [[Différenciation automatique]], dont le graphe de calcul n'est pas destiné à l'affichage.

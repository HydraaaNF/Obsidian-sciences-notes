Une **norme triangulaire** (ou **t-norme**), notée $\top$, est une opération
binaire sur $[0, 1]$ servant à définir l'[[Intersection d'ensembles flous]]
(conjonction).

### Propriétés caractéristiques
- **Commutativité** : $\top(x, y) = \top(y, x)$
- **Associativité** : $\top(x, \top(y, z)) = \top(\top(x, y), z)$
- **Monotonie** :
  - si $x_1 \leq x_2$ alors $\top(x_1, y) \leq \top(x_2, y)$
  - si $y_1 \leq y_2$ alors $\top(x, y_1) \leq \top(x, y_2)$
- **Élément neutre $1$** : $\top(1, x) = \top(x, 1) = x$

> [!warning] Correction
> L'élément neutre vérifie $\top(1, x) = x$, et non $\top(1, x) = 1$ : sinon
> $1$ serait un élément **absorbant**, pas neutre.

### Propriété de bornage
$$
\forall y, \quad \top(x, y) \leq x
\qquad\text{et}\qquad
\forall x, \quad \top(x, y) \leq y
$$

Une t-norme est donc toujours **plus exigeante** que chacun de ses arguments.

### Exemples
Il existe une **infinité** de t-normes. Les plus courantes :
- le **minimum** : $\top(x, y) = \min(x, y)$
- le **produit** : $\top(x, y) = x \cdot y$

Chaque t-norme est associée à une [[Conorme triangulaire]] par la
[[Dualité entre norme et conorme triangulaires]].
Une **conorme triangulaire** (ou **t-conorme**), notée $\bot$, est une opération
binaire sur $[0, 1]$ servant à définir l'[[Union d'ensembles flous]]
(disjonction).

### Propriétés caractéristiques
Symétriques de celles d'une [[Norme triangulaire]] :
- **Commutativité** : $\bot(x, y) = \bot(y, x)$
- **Associativité** : $\bot(x, \bot(y, z)) = \bot(\bot(x, y), z)$
- **Monotonie** (croissante en chaque argument)
- **Élément neutre $0$** : $\bot(0, x) = \bot(x, 0) = x$

### Propriété de bornage
$$
\forall y, \quad x \leq \bot(x, y)
\qquad\text{et}\qquad
\forall x, \quad y \leq \bot(x, y)
$$

Une t-conorme est donc toujours **plus permissive** que chacun de ses arguments.

### Exemples
- le **maximum** : $\bot(x, y) = \max(x, y)$
- la **somme probabiliste** : $\bot(x, y) = x + y - x \cdot y$

### Encadrement global
En combinant les deux bornages :

$$
\top(x, y) \leq x \leq \bot(x, y)
\qquad\text{et}\qquad
\top(x, y) \leq y \leq \bot(x, y)
$$
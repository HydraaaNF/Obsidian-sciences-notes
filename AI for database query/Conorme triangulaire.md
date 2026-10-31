# Définition
Une **conorme triangulaire** (ou **t-conorme**), notée $\bot$, est une opération binaire sur $[0, 1]$ servant à définir l'[[Union d'ensembles flous]] (disjonction).

# Propriétés
Symétriques de celles d'une [[Norme triangulaire]] :
- **Commutativité** : $\bot(x, y) = \bot(y, x)$
- **Associativité** : $\bot(x, \bot(y, z)) = \bot(\bot(x, y), z)$
- **Monotonie** : croissante en chaque argument
- **Élément neutre $0$** : $\bot(0, x) = \bot(x, 0) = x$
- **Élément absorbant $1$** : $\bot(x, 1) = \bot(1, y) = 1$
- **Bornage** :

$$
\forall y, \quad x \leq \bot(x, y)
\qquad\text{et}\qquad
\forall x, \quad y \leq \bot(x, y)
$$

- **Encadrement global** :

$$
\max(x, y) \leq \bot(x, y) \leq \bot_W(x, y)
$$

En combinant avec le bornage d'une t-norme :

$$
\top(x, y) \leq x \leq \bot(x, y)
\qquad\text{et}\qquad
\top(x, y) \leq y \leq \bot(x, y)
$$

# Interprétation
Une t-conorme est toujours **plus permissive** que chacun de ses arguments.

# Remarque
La plus petite t-conorme est le maximum (voir [[Minimum et maximum]]), la plus grande est la t-conorme de Weber (voir [[Norme et conorme de Weber]]). Les couples usuels sont présentés dans [[Couples usuels de normes et conormes triangulaires]].

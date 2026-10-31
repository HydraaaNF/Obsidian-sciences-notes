# Définition
Une **norme triangulaire** (ou **t-norme**), notée $\top$, est une opération binaire sur $[0, 1]$ servant à définir l'[[Intersection d'ensembles flous]] (conjonction).

# Propriétés
- **Commutativité** : $\top(x, y) = \top(y, x)$
- **Associativité** : $\top(x, \top(y, z)) = \top(\top(x, y), z)$
- **Monotonie** :
  - si $x_1 \leq x_2$ alors $\top(x_1, y) \leq \top(x_2, y)$ ;
  - si $y_1 \leq y_2$ alors $\top(x, y_1) \leq \top(x, y_2)$.
- **Élément neutre $1$** : $\top(1, x) = \top(x, 1) = x$
- **Élément absorbant $0$** : $\top(x, 0) = \top(0, y) = 0$
- **Bornage** :

$$
\forall y, \quad \top(x, y) \leq x
\qquad\text{et}\qquad
\forall x, \quad \top(x, y) \leq y
$$

- **Encadrement global** (voir [[Norme et conorme de Weber]] et [[Norme et conorme de Zadeh]]) :

$$
\top_W(x, y) \leq \top(x, y) \leq \min(x, y)
$$

# Interprétation
Une t-norme est toujours **plus exigeante** que chacun de ses arguments.

Elle **généralise la conjonction booléenne** : sur les valeurs $0$ et $1$, elle redonne la table de vérité du « et ».

| Égalité | Justification |
| --- | --- |
| $\top(0, 1) = \top(1, 0) = \top(0, 0) = 0$ | $0$ est absorbant |
| $\top(1, 1) = 1$ | $1$ est neutre |

# Remarque
Il existe une **infinité** de t-normes. Chacune est associée à une [[Conorme triangulaire]] par la [[Dualité entre norme et conorme triangulaires]]. Couples usuels : [[Norme et conorme de Zadeh]], [[Norme et conorme probabilistes]], [[Norme et conorme de Łukasiewicz]], [[Norme et conorme de Weber]].

Le choix du couple a des conséquences sur le résultat : voir l'effet de masque du minimum dans l'exemple de la [[Norme et conorme de Zadeh]], et l'[[Incompatibilité avec l'algèbre de Boole]].

La plus grande t-norme est le minimum (voir [[Norme et conorme de Zadeh]]), la plus petite est la t-norme de Weber (voir [[Norme et conorme de Weber]]).

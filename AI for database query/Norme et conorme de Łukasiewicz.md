# Définition
Le couple de **Łukasiewicz** est :

$$
\top(x, y) = \max(x + y - 1,\; 0) \qquad \bot(x, y) = \min(x + y,\; 1)
$$

Les deux opérations sont duales (voir [[Dualité entre norme et conorme triangulaires]]).

# Interprétation
Les deux opérations s'obtiennent en **additionnant** les degrés, puis en les **bornant** pour rester dans $[0, 1]$.

**La t-conorme : majoration par $1$.** La disjonction accumule les degrés : $x + y$. Or cette somme peut dépasser $1$, alors qu'un degré d'appartenance ne le peut pas. On majore donc par $1$ :

$$
\bot(x, y) = \min(x + y,\; 1)
$$

**La t-norme : minoration par $0$.** Par dualité (voir [[Dualité entre norme et conorme triangulaires]]), la conjonction se déduit de la disjonction. Elle revient à additionner les degrés puis à retrancher $1$, et on minore par $0$ pour ne pas obtenir de degré négatif :

$$
\top(x, y) = \max(x + y - 1,\; 0)
$$

### Démonstration
$$
\top(x, y) = 1 - \bot(1 - x,\; 1 - y) = 1 - \min\big(2 - x - y,\; 1\big) = \max\big(x + y - 1,\; 0\big)
$$

La dernière égalité vient de $1 - \min(a, b) = \max(1 - a,\; 1 - b)$.

**Lecture en termes de recouvrement.** Si $x$ et $y$ représentent deux portions d'un tout de taille $1$, la réunion est au plus de taille $x + y$ (cas où elles sont disjointes), plafonnée par la taille du tout. L'intersection est au moins de taille $x + y - 1$ (recouvrement minimal imposé par la taille du tout), et nulle si $x + y \leq 1$. Le couple de Łukasiewicz correspond ainsi au cas où les deux critères se recouvrent **le moins possible**.

# Remarque
Avec cette t-norme, la [[Différence d'ensembles flous]] devient $\mu_{E \setminus F}(x) = \max(\mu_E(x) - \mu_F(x),\; 0)$. Elle définit aussi l'[[Implication de Łukasiewicz]].

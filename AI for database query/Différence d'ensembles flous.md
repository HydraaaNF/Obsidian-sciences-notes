# Définition
Point de départ : $A \setminus B = \{x \mid x \in A \text{ et } x \notin B\}$.

Pour deux [[Ensemble flou|ensembles flous]] $E$ et $F$, avec une [[Norme triangulaire]] $\top$ quelconque :

$$
\forall x \in X, \quad \mu_{E \setminus F}(x) = \top\big(\mu_E(x),\; 1 - \mu_F(x)\big)
$$

Cela revient à intersecter $E$ avec le [[Complément d'un ensemble flou|complément]] de $F$.

# Propriétés
- Avec $\min$ : $\mu_{E \setminus F}(x) = \min(\mu_E(x),\; 1 - \mu_F(x))$.
- Avec la t-norme de Łukasiewicz : $\mu_{E \setminus F}(x) = \max(\mu_E(x) - \mu_F(x),\; 0)$ (voir [[Norme et conorme de Łukasiewicz]]).

# Exemple
Avec $E = \{1/a,\; 0{,}3/b,\; 0{,}7/c,\; 0{,}2/e\}$ et $F = \{0{,}3/a,\; 1/c,\; 1/d,\; 0{,}6/e\}$ :
- avec $\min$ : $E \setminus F = \{0{,}7/a,\; 0{,}3/b,\; 0{,}2/e\}$ ;
- avec Łukasiewicz : $E \setminus F = \{0{,}7/a,\; 0{,}3/b\}$.

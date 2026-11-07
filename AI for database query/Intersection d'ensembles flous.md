# Définition
L'**intersection** (conjonction) de deux [[Ensemble flou|ensembles flous]] $E$ et $F$ est définie au moyen d'une [[Norme triangulaire]] $\top$ :

$$
\forall x \in X, \quad \mu_{E \cap F}(x) = \top\big(\mu_E(x),\; \mu_F(x)\big)
$$

# Interprétation
Dans une [[Requête à préférences]], l'intersection correspond au **et** entre deux critères : le degré de satisfaction global ne peut pas dépasser le degré du critère le moins bien satisfait.

# Exemple
Soient $E = \{1/a,\; 0{,}3/b,\; 0{,}7/c,\; 0{,}2/e\}$ et $F = \{0{,}3/a,\; 1/c,\; 1/d,\; 0{,}6/e\}$.

| t-norme     | $E \cap F$                           |
| ----------- | ------------------------------------ |
| $\min$      | $\{0{,}3/a,\; 0{,}7/c,\; 0{,}2/e\}$  |
| produit     | $\{0{,}3/a,\; 0{,}7/c,\; 0{,}12/e\}$ |
| Łukasiewicz | $\{0{,}3/a,\; 0{,}7/c\}$             |

# Remarque
Opération duale : [[Union d'ensembles flous]]. Couples usuels de t-norme et t-conorme : [[Norme et conorme de Zadeh]], [[Norme et conorme probabilistes]], [[Norme et conorme de Łukasiewicz]], [[Norme et conorme de Weber]].

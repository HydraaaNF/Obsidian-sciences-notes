# Définition
L'**union** (disjonction) de deux [[Ensemble flou|ensembles flous]] $E$ et $F$ est définie au moyen d'une [[Conorme triangulaire]] $\bot$ :

$$
\forall x \in X, \quad \mu_{E \cup F}(x) = \bot\big(\mu_E(x),\; \mu_F(x)\big)
$$

# Interprétation
Dans une [[Requête à préférences]], l'union correspond au **ou** entre deux critères : le degré de satisfaction global est au moins égal au degré du critère le mieux satisfait.

# Exemple
Avec les mêmes $E$ et $F$ que dans [[Intersection d'ensembles flous]] :

| t-conorme | $E \cup F$ |
| --- | --- |
| $\max$ | $\{1/a,\; 0{,}3/b,\; 1/c,\; 1/d,\; 0{,}6/e\}$ |
| somme probabiliste | $\{1/a,\; 0{,}3/b,\; 1/c,\; 1/d,\; 0{,}68/e\}$ |
| Łukasiewicz | $\{1/a,\; 0{,}3/b,\; 1/c,\; 1/d,\; 0{,}8/e\}$ |

# Remarque
Opération duale : [[Intersection d'ensembles flous]].

# Définition
**Point de départ (cas classique).**

$$
(A \subset B) \iff (\forall x \in X,\; f_A(x) \leq f_B(x))
$$

**Extension directe aux [[Ensemble flou|ensembles flous]] :**

$$
(E \subset F) \iff (\forall x \in X,\; \mu_E(x) \leq \mu_F(x))
$$

C'est l'**inclusion au sens de Zadeh**.

# Interprétation
**Inconvénient.** Cette inclusion est booléenne : elle ne permet pas de discriminer des situations de non-inclusion très différentes.

# Exemple
Soient $E_1 = \{1/a,\; 1/b\}$, $E_2 = \{0{,}5/a,\; 0{,}7/b\}$ et $F = \{0{,}4/a,\; 0{,}7/b\}$.
- $E_1 \subset F$ ? **Non.**
- $E_2 \subset F$ ? **Non**, mais la non-inclusion est bien moins sévère que pour $E_1$.

# Remarque
Pour dépasser cette limite, voir l'[[Inclusion graduelle]].

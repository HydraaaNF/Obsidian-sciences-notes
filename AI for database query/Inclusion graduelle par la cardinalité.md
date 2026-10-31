# Définition
**Point de départ (cas classique).** $(A \subset B) \iff (A \cap B = A)$, d'où $(A \subset B) \iff (\operatorname{card}(A \cap B) = \operatorname{card}(A))$.

Pour $\operatorname{card}(A) > 0$, on définit :

$$
\deg(A \subset B) = \frac{\operatorname{card}(A \cap B)}{\operatorname{card}(A)}
$$

c'est-à-dire la proportion des éléments de $A$ qui sont aussi dans $B$.

**Extension aux ensembles flous**, pour $\operatorname{card}(E) > 0$ (voir [[Cardinalité d'un ensemble flou]]) :

$$
\deg(E \subset F) = \frac{\operatorname{card}(E \cap F)}{\operatorname{card}(E)} = \frac{\sum_{x \in X} \top\big(\mu_E(x),\; \mu_F(x)\big)}{\sum_{x \in X} \mu_E(x)}
$$

# Interprétation
- Avec $\top = \min$ : les degrés de $E$ jouent le rôle de **seuils** ([[Minimum et maximum]]).
- Avec $\top =$ produit : les degrés de $E$ jouent le rôle de **poids** (niveaux d'importance) ([[Produit et somme probabiliste]]) :

$$
\deg(E \subset F) = \frac{\sum_{x \in X} \mu_E(x) \times \mu_F(x)}{\sum_{x \in X} \mu_E(x)}
$$

# Remarque
Lorsque $E \subset F$ au sens de Zadeh ([[Inclusion de Zadeh]]), $\deg(E \subset F)$ n'est pas nécessairement égal à $1$ : cela dépend de la t-norme. Il vaut $1$ avec $\top = \min$, mais peut être inférieur à $1$ avec d'autres t-normes.

# Exemple
Soient $E = \{0{,}4/a,\; 0{,}6/b\}$ et $F = \{0{,}5/a,\; 1/b\}$. On a $E \subset F$ au sens de Zadeh.

- Avec $\top = \min$ : $\deg(E \subset F) = \dfrac{\min(0{,}4;\, 0{,}5) + \min(0{,}6;\, 1)}{0{,}4 + 0{,}6} = 1$
- Avec $\top =$ produit : $\deg(E \subset F) = \dfrac{0{,}4 \times 0{,}5 + 0{,}6 \times 1}{0{,}4 + 0{,}6} = 0{,}8$

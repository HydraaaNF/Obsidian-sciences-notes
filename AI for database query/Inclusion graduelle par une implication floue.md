# Définition
**Point de départ (cas classique).** $A \subset B \iff (\forall x \in X,\; x \in A \implies x \in B)$.

**Extension**, au moyen d'une [[Implication floue]] $\Rightarrow_f$ :

$$
\deg(E \subset F) = \min_{x \in X}\big(\mu_E(x) \Rightarrow_f \mu_F(x)\big)
$$

# Propriétés
La sémantique dépend du type d'implication ([[Implication de type S]] ou [[Implication de type R]]). Si $E \subset F$ au sens de Zadeh ([[Inclusion de Zadeh]]) :
- $\deg(E \subset F) = 1$ si une **R-implication** est utilisée ;
- $\deg(E \subset F)$ n'est pas nécessairement égal à $1$ avec une **S-implication**. Pour [[Implication de Kleene-Dienes|$\Rightarrow_{KD}$]] et [[Implication de Reichenbach|$\Rightarrow_{Rb}$]] : $\deg(E \subset F) = 1 \iff \operatorname{supp}(E) \subset \operatorname{noyau}(F)$.

# Exemple
Soient $E_1 = \{0{,}4/a,\; 0{,}7/b\}$, $E_2 = \{1/a,\; 0{,}9/b,\; 0{,}4/c\}$ et $F = \{1/a,\; 1/b,\; 0{,}5/c\}$. On a $E_1 \subset F$ et $E_2 \subset F$ au sens de Zadeh.

**Avec $\Rightarrow_{KD}$ :**

$$
\deg(E_1 \subset F) = \min\big(\max(1 - 0{,}4;\, 1),\; \max(1 - 0{,}7;\, 1),\; \max(1 - 0;\, 0{,}5)\big) = \min(1, 1, 1) = 1
$$

(en effet $\operatorname{supp}(E_1) = \{a, b\} \subset \operatorname{noyau}(F) = \{a, b\}$)

$$
\deg(E_2 \subset F) = \min\big(\max(1 - 1;\, 1),\; \max(1 - 0{,}9;\, 1),\; \max(1 - 0{,}4;\, 0{,}5)\big) = \min(1, 1, 0{,}6) = 0{,}6
$$

**Avec $\Rightarrow_{G\ddot{o}}$ :**
- $\deg(E_1 \subset F) = 1$
- $\deg(E_2 \subset F) = 1$

(car $\mu_{E_i}(x) \leq \mu_F(x)$ pour tout $x$ et $i \in \{1, 2\}$)

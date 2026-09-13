## Définition
Un **calcul** dans $A$ est une séquence de transitions $e_1...e_n$ de $A$, telle que pour tout couple de transitions successives $e_i , e_{i+1}$, l’état destination de $e_i$ est l’état origine de $e_{i+1}$. L’étiquette d’un **calcul** est le mot construit par concaténation des étiquettes de chacune des transitions.
- Un calcul dans $A$ est réussi si la première transition a pour origine l’état initial et la dernière transition a pour destination un des états finaux
- Le langage reconnu par l’automate $A$, noté $L(A)$, est l’ensemble des étiquettes des calculs réussis.
- Pour $a$ dans $\Sigma$ et $v$ dans $\Sigma^*$, pour noter une étape de calcul utilisant la transition $(q, a, \delta (q, a))$, on écrira $(q, av) \vdash_A (\delta (q, a), v)$
- La clôture réflexive et transitive de $\vdash_A$ se note $\vdash_A^*$ et on a $(q, uv) \vdash_A^* (p, v)$ s'il existe une suite d'états $q = q_1...q_n = p$ tels que $(q_1, u_1...u_nv) \vdash_A (q_2, u_2...u_nv)... \vdash_A (q_n, v)$ 
- Avec ces notations, on a : $$L(A) = \{u \in \Sigma^*|(q_0, u) \vdash_A^* (q, \epsilon), \text{ avec } q \in F\}$$

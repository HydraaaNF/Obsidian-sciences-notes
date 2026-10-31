# Définition
L'**implication de Łukasiewicz** est à la fois une S-implication et une R-implication.

**Comme S-implication**, avec la conorme $\bot(u, v) = \min(u + v,\; 1)$ :

$$
p \Rightarrow_{Lu} q = \min(1 - p + q,\; 1)
$$

**Comme R-implication**, avec la t-norme $\top(u, v) = \max(u + v - 1,\; 0)$ :

$$
p \Rightarrow_{Lu} q =
\begin{cases}
1 & \text{si } p \leq q \\
1 - p + q & \text{sinon}
\end{cases}
$$

# Remarque
C'est la **seule** de ces implications floues qui soit à la fois une [[Implication de type S]] et une [[Implication de type R]]. Voir [[Norme et conorme de Łukasiewicz]] et [[Comparaison des implications floues]].

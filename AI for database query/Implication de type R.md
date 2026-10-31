# Définition
Une **R-implication** utilise une [[Norme triangulaire]] $\top$ :

$$
(p \Rightarrow_R q) = \sup\{u \in [0, 1] \mid \top(p, u) \leq q\}
$$

Elle provient de l'équivalence ensembliste classique :

$$
\overline{A} \cup B = \overline{A \setminus B} = \bigcup \{Z \mid A \cap Z \subset B\}
$$

# Propriétés
Une R-implication peut aussi s'écrire :

$$
(p \Rightarrow_R q) =
\begin{cases}
1 & \text{si } p \leq q \\
f(p, q) & \text{sinon}
\end{cases}
$$

où $f$ est propre à la R-implication considérée.

# Exemple
R-implications usuelles :

| Nom | Définition | t-norme sous-jacente |
| --- | --- | --- |
| [[Implication de Gödel\|Gödel]] | $1$ si $p \leq q$, sinon $q$ | $\min(u, v)$ |
| [[Implication de Goguen\|Goguen]] | $1$ si $p \leq q$, sinon $q / p$ | $uv$ |
| [[Implication de Łukasiewicz\|Łukasiewicz]] | $1$ si $p \leq q$, sinon $1 - p + q$ | $\max(u + v - 1,\; 0)$ |

# Remarque
Voir [[Comparaison des implications floues]]. Famille duale : [[Implication de type S]].

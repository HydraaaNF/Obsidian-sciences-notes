# Définition
Dans le cas flou, la [[Division relationnelle]] s'écrit avec le degré d'inclusion de $s[B]$ dans $\Omega_r(x)$ :

$$
\mu_{r[A \div B]s}(x) = \deg\big(s[B] \subset \Omega_r(x)\big) \quad \text{avec } \mu_{\Omega_r(x)}(a) = \mu_{r[X, A]}(x, a)
$$

Lorsque l'inclusion est interprétée au moyen d'une [[Implication floue]] $\Rightarrow_f$ (voir [[Inclusion graduelle par une implication floue]]) :

$$
\mu_{r[A \div B]s}(x) = \min_{a \in s[B]}\Big(\mu_{s[B]}(a) \Rightarrow_f \mu_{r[X, A]}(x, a)\Big)
$$

# Exemple
Relation $r$ :

| X | A | $\mu$ |
| --- | --- | --- |
| x | $a_1$ | 0,7 |
| x | $a_2$ | 0,4 |
| x | $a_3$ | 1 |
| y | $a_1$ | 1 |
| y | $a_2$ | 0,6 |
| y | $a_3$ | 0,2 |

Relation $s$ :

| B | $\mu$ |
| --- | --- |
| $a_1$ | 1 |
| $a_2$ | 0,5 |
| $a_3$ | 0,3 |

Calcul de $r[A \div B]s$ avec les implications de Gödel, de Kleene-Dienes et de Łukasiewicz.

**Avec [[Implication de Gödel|Gödel]] :**

$$
\mu(x) = \min(1 \Rightarrow_{G\ddot{o}} 0{,}7;\ 0{,}5 \Rightarrow_{G\ddot{o}} 0{,}4;\ 0{,}3 \Rightarrow_{G\ddot{o}} 1) = \min(0{,}7;\ 0{,}4;\ 1) = 0{,}4
$$

$$
\mu(y) = \min(1 \Rightarrow_{G\ddot{o}} 1;\ 0{,}5 \Rightarrow_{G\ddot{o}} 0{,}6;\ 0{,}3 \Rightarrow_{G\ddot{o}} 0{,}2) = \min(1;\ 1;\ 0{,}2) = 0{,}2
$$

**Avec [[Implication de Kleene-Dienes|Kleene-Dienes]] :**

$$
\mu(x) = \min\big(\max(1 - 1;\ 0{,}7),\ \max(1 - 0{,}5;\ 0{,}4),\ \max(1 - 0{,}3;\ 1)\big) = \min(0{,}7;\ 0{,}5;\ 1) = 0{,}5
$$

$$
\mu(y) = \min\big(\max(1 - 1;\ 1),\ \max(1 - 0{,}5;\ 0{,}6),\ \max(1 - 0{,}3;\ 0{,}2)\big) = \min(1;\ 0{,}6;\ 0{,}7) = 0{,}6
$$

**Avec [[Implication de Łukasiewicz|Łukasiewicz]] :**

$$
\mu(x) = \min\big(\min(1 - 1 + 0{,}7;\ 1),\ \min(1 - 0{,}5 + 0{,}4;\ 1),\ \min(1 - 0{,}3 + 1;\ 1)\big) = \min(0{,}7;\ 0{,}9;\ 1) = 0{,}7
$$

$$
\mu(y) = \min\big(\min(1 - 1 + 1;\ 1),\ \min(1 - 0{,}5 + 0{,}6;\ 1),\ \min(1 - 0{,}3 + 0{,}2;\ 1)\big) = \min(1;\ 1;\ 0{,}9) = 0{,}9
$$

Récapitulatif :

| implication | $\mu(x)$ | $\mu(y)$ |
| --- | --- | --- |
| Gödel | 0,4 | 0,2 |
| Kleene-Dienes | 0,5 | 0,6 |
| Łukasiewicz | 0,7 | 0,9 |

# Remarque
Opérateur relationnel de l'[[Algèbre relationnelle floue]].

# Définition
La **cardinalité** (ou **$\Sigma$-count**) d'un [[Ensemble flou]] $E$ est le nombre d'éléments de $E$ **pondéré par leur degré d'appartenance** :

$$
\operatorname{card}(E) = \sum_{x \in X} \mu_E(x)
$$

# Exemple
Avec $E = \{1/a,\; 0{,}7/c,\; 0{,}2/e,\; 0{,}3/f,\; 0{,}6/h,\; 0{,}7/j,\; 0{,}9/k\}$ :

$$
\operatorname{card}(E) = 1 + 0{,}7 + 0{,}2 + 0{,}3 + 0{,}6 + 0{,}7 + 0{,}9 = 4{,}4
$$

# Remarque
Contrairement au cas classique, la cardinalité d'un ensemble flou n'est généralement **pas un entier**. On retrouve la cardinalité classique lorsque $\mu_E$ se réduit à l'[[Indicatrice]] : la somme compte alors exactement les éléments de degré $1$.

L'univers $X$ est supposé fini (voir [[Ensemble flou]]).

# Interprétation
La cardinalité est utilisée dans l'[[Inclusion graduelle par la cardinalité]] et dans l'[[Interprétation de Zadeh d'un énoncé quantifié flou]].

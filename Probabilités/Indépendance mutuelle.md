# Énoncé
Soit $(A_i)_{i \in I}$ une famille d'évènements. Ces évènements sont dits **mutuellement indépendants** si pour tout sous-ensemble **fini** $J$ inclus dans $I$, on a $p(\bigcap_{i \in J} A_i) = \prod_{i \in J} p(A_i)$

# Exemple : indépendance deux à deux n'implique pas l'indépendance mutuelle
On lance deux dés équilibrés. $\Omega = \{(i,j) \; ; \; 1 \leq i,j \leq 6\}$.

Soit $A$ = "le premier dé donne 1, 2 ou 3", $B$ = "le deuxième dé donne 4, 5 ou 6", $C$ = "la somme vaut 7". On a $\mathbb{P}(A) = \mathbb{P}(B) = \frac{3}{6}$ et $\mathbb{P}(C) = \frac{6}{36}$.

On vérifie que $A$, $B$, $C$ sont indépendants **deux à deux**, mais
$$\mathbb{P}(A \cap B \cap C) = \frac{1}{12} \neq \mathbb{P}(A)\mathbb{P}(B)\mathbb{P}(C) = \frac{1}{24}$$

# Remarque
Cet exemple montre que l'indépendance deux à deux (§[[Indépendance de deux évènements]]) est une condition strictement plus faible que l'indépendance mutuelle : il faut vérifier **toutes** les égalités de la définition, pas seulement celles portant sur des paires.

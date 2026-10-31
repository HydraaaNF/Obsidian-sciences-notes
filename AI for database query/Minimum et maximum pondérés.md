# Définition
Une version pondérée du couple [[Minimum et maximum]] a été proposée : $\operatorname{wmin}$ et $\operatorname{wmax}$.

Soient des poids (importances) $w_1, \ldots, w_n$ avec $\max_i w_i = 1$, associés aux ensembles flous $E_1, \ldots, E_n$ :

$$
\mu_{\operatorname{wmin}(E_1, \ldots, E_n;\, w_1, \ldots, w_n)}(x) = \min\big(\max(1 - w_1, \mu_{E_1}(x)),\; \ldots,\; \max(1 - w_n, \mu_{E_n}(x))\big)
$$

$$
\mu_{\operatorname{wmax}(E_1, \ldots, E_n;\, w_1, \ldots, w_n)}(x) = \max\big(\min(w_1, \mu_{E_1}(x)),\; \ldots,\; \min(w_n, \mu_{E_n}(x))\big)
$$

# Interprétation
Pour $\operatorname{wmin}$, un poids $w_i = 1$ conserve le degré $\mu_{E_i}(x)$, alors qu'un poids $w_i = 0$ donne $\max(1, \mu_{E_i}(x)) = 1$, qui est neutre pour le minimum : le critère est ignoré.

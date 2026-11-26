# Définition
On veut conserver l'équivalence entre :

```sql
SELECT * FROM r WHERE A θ ALL (SELECT B FROM s WHERE f_c)
```

et

```sql
SELECT * FROM r WHERE NOT EXISTS (SELECT B FROM s WHERE f_c AND NOT (A θ B))
```

où $f_c$ est une condition floue. Avec $E$ la [[Relation floue]] renvoyée par la sous-requête :

$$
\mu_{\theta\ \text{ALL}}(a, E) = 1 - \max_{b \in \operatorname{supp}(E)} \min\big(\mu_E(b);\ 1 - \mu_\theta(a, b)\big)
$$

Cette définition préserve les équivalences usuelles.

# Remarque
Cas de [[Imbrication avec ALL ou ANY]]. Opérateur dual : [[ANY flou]].

La formule s'écrit aussi :

$$
\mu_{\theta\ \text{ALL}}(a, E) = \min_{b \in \operatorname{supp}(E)} \max\big(1 - \mu_E(b);\ \mu_\theta(a, b)\big) = \min_{b \in \operatorname{supp}(E)} \big(\mu_E(b) \Rightarrow_{KD} \mu_\theta(a, b)\big)
$$

C'est le degré d'[[Inclusion graduelle par une implication floue]] de $E$ dans l'ensemble flou des $b$ tels que $a\ \theta\ b$ (de degré $\mu_\theta(a, b)$), avec l'[[Implication de Kleene-Dienes]]. Les éléments hors de $\operatorname{supp}(E)$, de degré $0$, donnent une implication égale à $1$ et n'influent pas sur le minimum.

### Démonstration
$$
1 - \max_b \min(u_b;\ 1 - v_b) = \min_b \big(1 - \min(u_b;\ 1 - v_b)\big) = \min_b \max(1 - u_b;\ v_b)
$$

avec $u_b = \mu_E(b)$ et $v_b = \mu_\theta(a, b)$ ; la dernière égalité vient de $1 - \min(x, y) = \max(1 - x,\ 1 - y)$.

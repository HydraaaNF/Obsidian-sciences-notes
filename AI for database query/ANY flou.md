# Définition
On veut conserver l'équivalence entre :

```sql
SELECT * FROM r WHERE A θ ANY (SELECT B FROM s WHERE f_c)
```

et

```sql
SELECT * FROM r WHERE EXISTS (SELECT B FROM s WHERE f_c AND A θ B)
```

où $f_c$ est une condition floue. Avec $E$ la [[Relation floue]] renvoyée par la sous-requête :

$$
\mu_{\theta\ \text{ANY}}(a, E) = \max_{b \in \operatorname{supp}(E)} \min\big(\mu_E(b);\ \mu_\theta(a, b)\big)
$$

# Remarque
Cette valeur est la hauteur (voir [[EXISTS flou]]) de l'ensemble flou des $b$ de degré $\min(\mu_E(b);\ \mu_\theta(a, b))$. Cas de [[Imbrication avec ALL ou ANY]]. Opérateur dual : [[ALL flou]].

# Définition
**Cas classique.** `IN` est fondé sur l'égalité. L'opérateur $\text{IN}_f$ est fondé sur l'**égalité approchée** $\approx$.

Pour une [[Relation floue]] $E$ renvoyée par la sous-requête :

$$
\mu_{\text{IN}_f}(a, E) = \max_{b \in \operatorname{supp}(E)} \min\big(\mu_{\approx}(a, b);\ \mu_E(b)\big)
$$

# Propriétés
**Égalité approchée.** Pour $\delta_1 < \delta_2$ :

$$
\mu_{\approx}(x, y) =
\begin{cases}
1 & \text{si } \lvert x - y \rvert \leq \delta_1 \\
0 & \text{si } \lvert x - y \rvert \geq \delta_2 \\
\dfrac{\delta_2 - \lvert x - y \rvert}{\delta_2 - \delta_1} & \text{sinon (linéaire entre les deux)}
\end{cases}
$$

En fonction de $\lvert x - y \rvert$, c'est un trapèze (voir [[Fonction d'appartenance trapézoïdale]]) : égal à $1$ jusqu'à $\delta_1$, puis linéairement décroissant jusqu'à $0$ en $\delta_2$, puis égal à $0$.

# Exemple
```sql
SELECT #e FROM Emp
WHERE salaire * 1000 IN_f (SELECT budget FROM Dep WHERE #d = Emp.dep)
```

Cette requête est équivalente à :

```sql
SELECT #e FROM Emp, Dep
WHERE Emp.dep = Dep.#d AND budget ≈ 1000 * salaire
```

# Remarque
Première extension de `IN` : [[IN avec sous-requête floue]].

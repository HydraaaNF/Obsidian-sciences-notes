# Définition
**Cas classique.** `IN` teste l'appartenance d'une valeur d'attribut à l'ensemble des valeurs renvoyées par une sous-requête.

```sql
SELECT #e FROM Emp
WHERE âge < 35 AND dep IN (SELECT #d FROM Dep WHERE budget > 100k)
```

Cette requête est équivalente à la jointure :

```sql
SELECT #e FROM Emp, Dep
WHERE Emp.dep = Dep.#d AND âge < 35 AND budget > 100k
```

**Cas flou : sous-requête floue.** La sous-requête renvoie une [[Relation floue]] $E$ :

```sql
SELECT #e FROM Emp
WHERE âge IS jeune AND dep IN (SELECT #d FROM Dep WHERE budget IS élevé)
```

Le degré d'appartenance de $a$ à $E$ est :

$$
\mu_{\text{IN}}(a, E) =
\begin{cases}
0 & \text{si } a \notin \operatorname{supp}(E) \\
\max\{\mu \mid \mu / a \in E\} & \text{sinon}
\end{cases}
$$

Le degré d'un employé $e$ dans le résultat est :

$$
\min\big(\mu_{\text{jeune}}(e.\text{âge});\ \mu_{\text{IN}}(e.\text{dep},\ SQ)\big)
$$

où $SQ$ est la sous-requête.

# Propriétés
La formulation par jointure donne le même résultat :

```sql
SELECT #e FROM Emp, Dep
WHERE âge IS jeune AND budget IS élevé AND Emp.dep = Dep.#d
```

Le degré d'un employé $e$ dans le résultat est alors :

$$
\min\Big(\mu_{\text{jeune}}(e.\text{âge});\ \max_{t \in \text{Dep}}\big(\min(\mu_{\text{élevé}}(t.\text{budget});\ \mu_{=}(t.\#d,\ e.\text{dep}))\big)\Big)
$$

où $\mu_{=}$ est l'égalité usuelle (nette).

Pour la négation :

$$
\mu_{\text{NOT IN}}(a, E) = 1 - \mu_{\text{IN}}(a, E)
$$

# Remarque
Seconde extension de `IN`, fondée sur l'égalité approchée : [[IN flou]].

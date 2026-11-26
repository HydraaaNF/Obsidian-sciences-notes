# Définition
**Cas classique.** `EXISTS` teste si le résultat d'une sous-requête est non vide.

```sql
SELECT #d FROM Dep
WHERE EXISTS (SELECT * FROM Emp WHERE dep = #d AND âge < 35)
```

Cette requête est équivalente à :

```sql
SELECT #d FROM Dep
WHERE #d IN (SELECT dep FROM Emp WHERE âge < 35)
```

**Cas flou.** Il faut évaluer la non-vacuité d'un [[Ensemble flou]]. Deux façons :
- **quantitative** : fondée sur la [[Cardinalité d'un ensemble flou]] ;
- **qualitative** : fondée sur la [[Hauteur d'un ensemble flou]].

La seconde préserve les équivalences usuelles :

$$
\mu_{\text{EXISTS}}(E) = \max_{x \in \operatorname{supp}(E)} \mu_E(x) = \operatorname{hauteur}(E)
$$

avec $\mu_{\text{EXISTS}}(E) = 0$ si $E$ est vide.

# Propriétés
$$
\mu_{\text{NOT EXISTS}}(E) = 1 - \mu_{\text{EXISTS}}(E)
$$

# Remarque
Voir [[SQLf]]. L'évaluation de `ANY` et `ALL` s'appuie sur `EXISTS` : [[ANY flou]], [[ALL flou]].

# Définition
**Cas SQL.** Une relation peut être partitionnée avec la clause `GROUP BY`. Une condition sur les groupes s'exprime avec la clause `HAVING`.

```sql
SELECT dep FROM Emp GROUP BY dep HAVING avg(salaire) > 3000
```

# Propriétés
En SQLf :
- la clause `GROUP BY` ne change pas ;
- dans la clause `HAVING`, une condition floue peut comparer un agrégat à une constante ou à un autre agrégat.

La clause `WHERE` d'une telle requête ne peut pas contenir de condition floue (une condition non floue peut y figurer).

# Exemple
Avec le comparateur flou $\gg$ (« nettement supérieur à ») :

```sql
SELECT dep FROM Emp GROUP BY dep HAVING avg(salaire) >> 3000
```

# Remarque
Voir [[SQLf]] et [[Bloc multirelation de SQLf]].

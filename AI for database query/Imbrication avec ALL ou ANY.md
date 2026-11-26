# Définition
En SQL, la condition `A θ {ALL | ANY} SQ` compare une valeur $A$ au résultat d'une sous-requête $SQ$ au moyen d'un comparateur $\theta$.

- `A θ ANY (SQ)` vaut $1$ s'il existe un élément $x$ du résultat de $SQ$ tel que $A\ \theta\ x$, et $0$ sinon.
- `A θ ALL (SQ)` vaut $1$ si, pour tout élément $x$ du résultat de $SQ$, $A\ \theta\ x$, et $0$ sinon.

# Propriétés
Trois façons d'étendre ces conditions :
- la sous-requête $SQ$ peut être floue ;
- un [[Quantificateur flou]] peut remplacer `ALL` et `ANY` ;
- le comparateur $\theta$ peut être flou.

Formules pour une sous-requête floue : [[ANY flou]] et [[ALL flou]].

# Exemple
Avec le comparateur flou $\gg$ (« nettement supérieur à »), on cherche les employés dont le salaire est nettement supérieur à celui des autres employés du même département :

```sql
SELECT #e FROM Emp E1
WHERE E1.salaire >> ALL (SELECT E2.salaire FROM Emp E2
                         WHERE E2.dep = E1.dep AND E2.#e <> E1.#e)
```

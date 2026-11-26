# Définition
En SQL, il n'existe **pas d'opérateur spécifique** pour la [[Division relationnelle]]. Deux possibilités : la **double imbrication** ou la **comparaison de cardinalités**.

# Exemple
Relations :
- fournisseurs $S(\#f, \text{nom}, \text{âge}, \text{ville})$ ;
- produits $P(\#p, \text{nom}, \text{couleur}, \text{origine})$ ;
- fournitures $M(\#f, \#p, \text{qté})$.

Requête : *trouver les fournisseurs qui fournissent tous les produits verts de $P$.*

En algèbre relationnelle :

$$
M[\#f, \#p]\ [\#p \div \#p]\ \sigma_{\text{couleur} = \text{« vert »}}(P)
$$

**Double imbrication :**

```sql
SELECT #f FROM S
WHERE NOT EXISTS (SELECT * FROM P
                  WHERE P.couleur = 'vert'
                    AND P.#p NOT IN (SELECT M.#p FROM M WHERE M.#f = S.#f))
```

**Comparaison de cardinalités :**

```sql
SELECT #f FROM M
WHERE #p IN (SELECT #p FROM P WHERE couleur = 'vert')
GROUP BY #f
HAVING COUNT(*) = (SELECT COUNT(*) FROM P WHERE couleur = 'vert')
```

# Remarque
Version en SQLf : [[Division en SQLf]]. Ancien opérateur SQL dédié : [[Opérateur CONTAINS]].

# Définition
Une ancienne version de SQL comportait l'opérateur **`CONTAINS`**, qui teste l'**inclusion d'un ensemble dans un autre**.

# Exemple
Fournisseurs qui fournissent tous les produits verts (voir [[Division en SQL]]) :

```sql
SELECT #f FROM M GROUP BY #f
HAVING set(#p) CONTAINS (SELECT #p FROM P WHERE couleur = 'vert')
```

# Remarque
Version floue : [[Division en SQLf]].

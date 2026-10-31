# Définition
Un SGBD ne comprend que des **requêtes booléennes** : un n-uplet satisfait la condition ou ne la satisfait pas. Une requête exprimée en langage naturel doit donc être traduite en une condition stricte (*crisp*), par exemple en SQL.

# Exemple
Besoin : *« un restaurant asiatique, pas trop cher, proche du centre-ville »*.

Traduction booléenne (SQL) :

```
type = 'chinese' AND price <= 25 AND dist_center <= 2
```

# Remarque
Cette traduction présente plusieurs inconvénients :
- **risque de réponse vide** : aucun n-uplet ne franchit tous les seuils ;
- **risque de réponse pléthorique** : trop de n-uplets, sans moyen de les ordonner ;
- **sensibilité aux seuils** : un restaurant à $25{,}5$ € est rejeté exactement comme un restaurant à $200$ €.

Ces limites motivent les [[Requête à préférences|requêtes à préférences]].

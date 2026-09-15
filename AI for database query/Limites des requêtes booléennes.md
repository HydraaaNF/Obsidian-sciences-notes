Un SGBD ne comprend que des **requêtes booléennes** : un n-uplet satisfait la
condition ou ne la satisfait pas. Un besoin utilisateur exprimé en langage
naturel doit donc être traduit en conditions à seuils.

### Exemple
Besoin : *« un restaurant asiatique, pas trop cher, proche du centre-ville »*

Traduction booléenne :
`type = "chinois" and prix <= 25 and dist_centre <= 1km`

### Inconvénients
- **Risque de réponse vide** : aucun n-uplet ne franchit tous les seuils
- **Risque de réponse pléthorique** : trop de n-uplets, sans moyen de les
  ordonner par pertinence
- **Sensibilité aux seuils** : un restaurant à 25,50 € est rejeté au même titre
  qu'un restaurant à 90 €, alors que l'écart de satisfaction est incomparable

Ces limites motivent les [[Requête à préférences|requêtes à préférences]].
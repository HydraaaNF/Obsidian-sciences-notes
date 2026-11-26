# Définition
**SQLf** est l'extension floue du langage SQL. Elle s'appuie sur l'[[Algèbre relationnelle floue]] et manipule des [[Relation floue|relations floues]].

# Propriétés
Les opérateurs flous de SQLf sont définis de sorte que les **équivalences usuelles entre requêtes soient préservées** :
- `IN` et jointure : [[IN avec sous-requête floue]] ;
- `EXISTS` et `IN` : [[EXISTS flou]] ;
- `ANY` et `EXISTS` : [[ANY flou]] ;
- `ALL` et `NOT EXISTS` : [[ALL flou]].

# Remarque
Éléments de SQLf : le [[Bloc multirelation de SQLf]], le [[Partitionnement d'une relation dans SQLf]], les requêtes imbriquées ([[IN avec sous-requête floue]], [[IN flou]], [[EXISTS flou]], [[Imbrication avec ALL ou ANY]]) et la division ([[Division en SQLf]]).

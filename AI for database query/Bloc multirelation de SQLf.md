# Définition
En SQL, un **bloc multirelation** est une requête de la forme :

```sql
SELECT <attributs> FROM <relations> WHERE <condition booléenne>
```

Ce sont des requêtes sélection-projection-jointure (voir [[Sélection floue]], [[Projection floue]], [[Jointure floue]] pour leurs versions floues). Les doublons sont éliminés en présence de `DISTINCT`.

# Propriétés
En SQLf, deux éléments changent :
- un **paramètre supplémentaire** filtre le résultat :
  - **filtrage quantitatif** : un entier $k$ (on veut les $k$ meilleures réponses) ;
  - **filtrage qualitatif** : un seuil $\alpha \in\ ]0, 1]$ (on ne veut que les réponses dont le degré est $\geq \alpha$) ;
  - ou les deux ;
- la clause `WHERE` peut contenir une **condition floue**.

```sql
SELECT [k | α | k, α] <attributs> FROM <relations> WHERE <condition floue>
```

# Remarque
Bloc de base de [[SQLf]].

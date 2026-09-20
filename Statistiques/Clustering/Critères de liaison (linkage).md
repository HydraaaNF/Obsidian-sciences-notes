# Définition
Le critère de liaison (*linkage*) détermine comment mesurer la distance entre deux clusters $A$ et $B$ en [[Classification ascendante hiérarchique|classification ascendante hiérarchique]] :

- **liaison simple** (*single linkage*) : $D(A,B) = \min(d(x,y),\ \forall (x,y) \in A \times B)$ — adaptée aux classes bien séparées uniquement
- **liaison complète** (*total/complete linkage*) : $D(A,B) = \max(d(x,y),\ \forall (x,y) \in A \times B)$ — favorise les grands clusters
- **liaison moyenne** (*average linkage*) : distance moyenne entre tous les éléments de $A$ et de $B$ — robuste au bruit et aux valeurs aberrantes, mais biaisée vers des clusters globulaires
- **liaison de Ward** : augmentation de la variance induite par la fusion des deux clusters

# Remarque
D'autres critères existent, notamment la distance entre moyennes/médianes, ou entre modèles statistiques des données.

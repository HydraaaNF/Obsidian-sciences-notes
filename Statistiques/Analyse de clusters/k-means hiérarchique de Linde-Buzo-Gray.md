# Algorithme

Le **k-means hiérarchique**, algorithme original de **Linde-Buzo-Gray** (LBG), aussi appelé *bisecting k-means*, est une variante du [[k-means]] qui construit les clusters par divisions successives.

Partant d'un centroïde placé au centre de gravité, il scinde répétitivement chaque centroïde le long de la ligne de variance maximale et exécute l'[[Algorithme des k-moyennes de Lloyd|algorithme des k-moyennes]] après chaque scission, tant que le nombre de clusters est insuffisant :

```
initialiser les centroïdes c_1(1) au centre de gravité
i ← 1
tant que pas assez de clusters (i < p) faire
    scinder chaque centroïde c_i(j) (selon la ligne de variance maximale)
    exécuter k-means
fin tant que
```

Ses nombreuses variantes adaptent ce schéma :

- ne scinder que le plus gros cluster : le nombre de clusters devient arbitraire au lieu de $2^p$ ;
- garder les points dans leur cluster parent : l'algorithme est bien plus rapide.

# Interprétation

Le k-means hiérarchique remédie au caractère délicat de l'initialisation du [[k-means]] : à côté du choix aléatoire des centroïdes ou des exécutions multiples (voir [[Propriétés du k-means]]), il construit progressivement les centroïdes en divisant les clusters.

# Remarque

Par ses divisions successives de clusters, le k-means hiérarchique est à rapprocher du [[Clustering hiérarchique|clustering hiérarchique]].

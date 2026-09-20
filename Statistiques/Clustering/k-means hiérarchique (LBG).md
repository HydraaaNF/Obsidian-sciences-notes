# Définition
Méthode d'initialisation du [[k-means]] en construisant progressivement les clusters par divisions successives, aussi appelée **bisecting k-means**.

# Algorithme (Linde-Buzo-Gray)
```
initialiser le centroïde c_1(1) au centre de gravité des données
i ← 1
tant que pas assez de clusters (i < p) :
    diviser chaque centroïde c_i(j) (le long de la ligne de variance maximale)
    exécuter k-means
```

# Remarque
Plusieurs variantes existent :
- ne diviser que le plus grand cluster → nombre de clusters arbitraire au lieu de $2^p$
- garder les points dans leur cluster parent → beaucoup plus rapide

Dans tous les cas, la solution obtenue reste un **optimum local**.

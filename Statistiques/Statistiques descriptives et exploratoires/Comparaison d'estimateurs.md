# Définition

Il est possible de comparer des [[Estimateur|estimateurs]] sur la base de leur [[Risque généralisé|risque]], même si la fonction de risque est rarement facile à définir.

Un estimateur $T$ est **meilleur** qu'un estimateur $T'$ si

$$R(T, \theta) < R(T', \theta) \quad \forall \theta \in \Theta.$$

# Interprétation

Il est en général impossible de trouver un estimateur $T$ meilleur que tout autre pour toutes les valeurs de $\theta$ : un estimateur constant en donne une illustration. Sauf dans quelques cas très particuliers, il existe rarement un estimateur uniformément meilleur que tous les autres.

# Remarque

Le risque retenu pour la comparaison peut être l'[[Erreur quadratique moyenne]]. Faute d'un estimateur uniformément meilleur, la comparaison est souvent restreinte à une classe d'estimateurs, par exemple celle des [[Biais d'un estimateur|estimateurs sans biais]], ce qui conduit à la recherche d'un [[Estimateur sans biais de variance minimale]].

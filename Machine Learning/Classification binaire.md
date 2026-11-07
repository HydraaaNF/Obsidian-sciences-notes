#ml-1

# Modèle

Un jeu de données de classification binaire est un ensemble de points $(x_1, x_2, y)$ où :

- les $x_i$ sont des variables numériques ;
- $y$ est une variable **binaire**.

Le problème consiste à trouver une fonction $f$ telle que $f(x)$ soit aussi proche que possible de $y$.

L'énoncé est le même que celui de la [[Régression linéaire]], mais $y$ vit désormais dans $\{0, 1\}$, et cela change tout.

# Remarque

Rien n'empêche d'ajuster $ax + b$ sur $y \in \{0, 1\}$, mais deux obstacles s'y opposent :

- la sortie est **non bornée** : $f(x) = 1.4$ ne signifie rien de précis, $f(x) = -0.3$ encore moins ;
- la [[Perte absolue et perte quadratique|perte quadratique]] continue de **pénaliser** des points déjà corrects : un point correct situé loin tire toute la droite à lui.

Il faut donc une sortie qui soit une **probabilité** ; c'est ce que construit la [[Régression logistique]].

La classification binaire est le cas à deux classes de la classification, dont la typologie est décrite dans [[Types de classification]] ; elle relève des [[Problèmes d'apprentissage statistique]].

# Algorithme

L'**algorithme des k-moyennes de Lloyd** fournit une solution approchée du problème du [[k-means]].

**Idée :** diviser des données $x_i$ en $K$ clusters représentés par la valeur moyenne de leurs membres $c_k$ (centroïdes), de façon à minimiser l'erreur de quantification globale :

$$e = \sum_i d(x_i, c_{f(i)})$$

L'algorithme alterne, jusqu'à convergence, une phase d'affectation et une phase de mise à jour :

```
initialiser K centroïdes c_k
tant que non convergé faire
  pour i = 1 → N faire
    affecter x_i au centroïde le plus proche (f(i) ← arg min_k d(x_i, c_k))
  fin pour
  pour i = 1 → K faire
    mettre à jour le centroïde c_k à partir de tous les points affectés
  fin pour
fin tant que
```

# Exemple

L'exécution de l'algorithme est illustrée sur un nuage de points du plan, en six itérations : les points sont colorés selon le centroïde qui leur est affecté et les croix marquent la position des centroïdes.

À la première itération, les trois centroïdes sont proches les uns des autres ; au fil des itérations, chacun se déplace vers la moyenne des points qui lui sont affectés et certaines affectations changent. La configuration se stabilise ensuite : les points finissent répartis en trois groupes nettement séparés, en haut au centre, en bas à gauche et en bas à droite, chaque centroïde venant se placer au centre de son groupe.

# Remarque

Les [[Propriétés du k-means|propriétés du k-means]] précisent la convergence et la complexité de l'algorithme ainsi que le rôle de son initialisation, et le [[Choix du nombre de clusters|choix du nombre de clusters]] traite la détermination du nombre $K$ de clusters.

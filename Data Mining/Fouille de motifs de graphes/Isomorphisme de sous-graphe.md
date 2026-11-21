#dmv-graph_mining

# Définition

Soient deux graphes étiquetés $G_1 = (V_1, E_1, l_1)$ et $G_2 = (V_2, E_2, l_2)$.

$G_1$ est sous-graphe isomorphe à $G_2$ s'il existe un graphe $G'$ tel que :

- $G'$ est isomorphe à $G_1$
- $G'$ est un sous-graphe de $G_2$

Forme explicite : $G_1$ est sous-graphe isomorphe à $G_2$ s'il existe une injection $f \colon V_1 \to V_2$ telle que :

$$\forall e = (u, v) \in E_1,\ (f(u), f(v)) \in E_2$$

$$\forall v \in V_1,\ l_2(f(v)) = l_1(v)$$

$$\forall e = (u, v) \in E_1,\ l_2((f(u), f(v))) = l_1((u, v))$$

# Interprétation

Reconnaître si un graphe est une partie d'un autre graphe : l'injection apparie chaque sommet du graphe cherché à un sommet distinct du graphe hôte, de même étiquette, en conservant les arêtes et leurs étiquettes.

L'injection n'est pas une bijection : le graphe hôte peut posséder d'autres sommets et d'autres arêtes que ceux retenus par $f$, ce qui correspond au graphe $G'$ de la définition.

L'isomorphisme de sous-graphe généralise l'[[Isomorphisme de graphes]] : la bijection y devient une injection, et le graphe cherché n'a plus à couvrir tout le graphe hôte.

# Remarque

La recherche d'un sous-graphe isomorphe est NP-complète.

En pratique, si les étiquettes sont suffisamment variées, le calcul reste faisable en temps raisonnable : chaque sommet ne peut être apparié qu'aux sommets portant la même étiquette, ce qui réduit fortement le nombre d'appariements à essayer.

#dmv-graph_mining

# Définition

Soient deux graphes étiquetés $G_1 = (V_1, E_1, l_1)$ et $G_2 = (V_2, E_2, l_2)$.

$G_1$ est isomorphe à $G_2$ s'il existe une bijection $f \colon V_1 \to V_2$ telle que :

$$\forall v_1 \in V_1,\ l_1(v_1) = l_2(f(v_1))$$

$$\forall (v_1, u_1) \in E_1,\ (f(v_1), f(u_1)) \in E_2$$

$$\forall (v_1, u_1) \in E_1,\ l_2((f(v_1), f(u_1))) = l_1((v_1, u_1))$$

# Interprétation

Reconnaître si deux [[Graphe|graphes]] sont les mêmes, c'est-à-dire si leurs sommets peuvent être appariés deux à deux sans changer la structure : la bijection $f$ apparie les sommets, la première condition impose des étiquettes identiques, la deuxième la conservation de l'adjacence, la troisième celle des étiquettes d'arêtes.

Des graphes peuvent sembler différents, dessinés autrement et avec d'autres noms de sommets, et avoir en réalité la même structure : l'isomorphisme compare la structure, pas la disposition du dessin.

# Exemple

Le graphe biparti $G$, dont les sommets se répartissent en $a, b, c, d$ d'une part et $g, h, i, j$ d'autre part, est isomorphe au graphe cube $H$, dont les sommets sont numérotés de $1$ à $8$. Un isomorphisme entre les deux :

| Sommet de $G$ | Sommet de $H$ |
| :---: | :---: |
| $a$ | $1$ |
| $b$ | $6$ |
| $c$ | $8$ |
| $d$ | $3$ |
| $g$ | $5$ |
| $h$ | $2$ |
| $i$ | $4$ |
| $j$ | $7$ |

# Remarque

La recherche d'un graphe à l'intérieur d'un autre, où le graphe cherché ne couvre qu'une partie du graphe hôte, relève de l'[[Isomorphisme de sous-graphe]].

Les étiquettes comparées dépendent du type de graphe considéré (voir [[Types de graphes]]) : un graphe étiqueté porte une fonction d'étiquetage sur ses sommets et ses arêtes, et l'isomorphisme doit la respecter.

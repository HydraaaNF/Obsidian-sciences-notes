# Modèle
- Données : exemples $\{x_1, \ldots, x_N\}$, avec $x_i \in \mathbb{R}^d$
- Clusters : centres $\{c_1, \ldots, c_K\}$, avec $c_i \in \mathbb{R}^d$
- Fonction d'assignation $f : [1,N] \to [1,K]$, où $f(i)$ est l'indice du cluster/centre assigné à l'exemple $i$
- Cluster $S_k = \{x_i : f(i) = k\}$
- **Inertie** : $\displaystyle\sum_k \sum_{x \in S_k} \|x - c_k\|^2$

# Objectif
Le k-means est une **formulation de problème**, pas un algorithme en soi.

**Problème** : étant donné un espace/une distance euclidienne et $k$ le nombre de clusters souhaité, trouver les centres qui minimisent la somme des carrés des distances de chaque point à son centre.

Trouver une solution exacte est **NP-difficile** ; on utilise en pratique une solution approchée : l'**algorithme de Lloyd** (souvent appelé lui-même « algorithme des k-means »).

# Algorithme (algorithme de Lloyd)
Idée : diviser les données $x_i$ en $K$ clusters représentés par la valeur moyenne de leurs membres $c_k$ (centroïdes), pour minimiser l'erreur de quantification globale $e = \sum_i d(x_i, c_{f(i)})$.

```
initialiser K centroïdes c_k
tant que non convergé :
    pour i = 1 à N :
        assigner x_i au centroïde le plus proche (f(i) ← argmin_k d(x_i, c_k))
    pour k = 1 à K :
        mettre à jour c_k à partir de tous les points assignés
```

# Remarques
- Le choix de la distance est déterminant : la **moyenne** doit avoir un sens pour la distance choisie ; sinon on peut utiliser la médiane — voir [[k-médianes et k-médoïdes]]
- **Convergence** : garantie, généralement en 10 à 20 itérations (convergence = plus rien ne bouge)
- **Complexité** : $O(iKNd)$, où $i$ = nombre d'itérations, $d$ = dimension des $x_i$
- **Initialisation** : point sensible — voir choix aléatoire, exécutions multiples, ou [[k-means hiérarchique (LBG)]]
- Pour choisir $K$, voir [[Choix du nombre de clusters (méthode du coude)]]

# Avantages / Inconvénients
**Avantages** : simple, populaire, efficace, convergence garantie, s'adapte à toute forme avec suffisamment de clusters

**Inconvénients** : sensible à l'initialisation et aux optima locaux, nécessite de fixer $K$ à l'avance, favorise les clusters convexes de taille/densité comparable, tend à créer des cellules déséquilibrées, très sensible au bruit et aux valeurs aberrantes

# Référence
J. B. McQueen. *Some methods for classification and analysis of multivariate observations*. Proc. Symposium on Math., Statistics, and Probability, pp. 281-297, 1967.

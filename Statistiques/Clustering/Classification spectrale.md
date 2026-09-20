# Définition
Méthode de clustering fondée sur les propriétés spectrales du [[Laplacien d'un graphe|Laplacien]] d'un graphe de similarité construit à partir des données.

# Graphe de similarité
Chaque point de donnée devient un nœud du graphe ; les arêtes encodent la similarité entre deux nœuds via des poids $w_{ij}$. Constructions courantes :
- graphe des $\varepsilon$-voisins
- graphe des $k$ plus proches voisins
- graphe complètement connecté

# Algorithme
Entrée : matrice de similarité $S \in \mathbb{R}^{n \times n}$, nombre de clusters $k$
```
construire un graphe de similarité à partir de S, de matrice d'adjacence W
calculer le Laplacien L
calculer les k vecteurs propres u_1, ..., u_k de L associés aux k plus petites valeurs propres
définir U ∈ R^(n×k) avec u_1, ..., u_k comme colonnes
définir y_i ∈ R^k la i-ème ligne de U, pour i ∈ [1, n]
exécuter k-means (ou une autre méthode) sur les vecteurs y_i
```

# Remarque
Liens forts avec les algorithmes de coupe de graphe (NCut, RatioCut, MinMaxCut) et la théorie des marches aléatoires (*Markov clustering*).

# Avantages / Inconvénients (par rapport à DBSCAN)
**Avantages** : personnalisation de la matrice d'affinité selon des connaissances du domaine, moins sensible aux paramètres de localité (conserve plus de connexions, laisse le [[k-means]] final écarter les moins importantes), gère mieux des clusters de densités variées

**Inconvénients** : sensible au réglage des paramètres (y compris le choix de la matrice d'affinité), complexité calculatoire plus élevée, ne gère pas le bruit et les valeurs aberrantes, nécessite de fixer le nombre de clusters à l'avance

# Référence
Ulrike von Luxburg. *A tutorial on spectral clustering*. Statistics and Computing, 17(4):395-416, 2007.

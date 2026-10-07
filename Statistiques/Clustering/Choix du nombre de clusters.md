# Interprétation

Le nombre de clusters n'est pas une notion objective : les mêmes données peuvent être décrites par plusieurs [[Types de clustering|partitionnements]] également plausibles. Sur un même ensemble de points en deux dimensions, on peut ainsi mettre en évidence six, deux ou quatre clusters (chaque groupe distingué par un symbole différent) sans qu'un découpage s'impose comme le seul correct.

La valeur de $k$ n'est donc pas fournie par les données ; elle se choisit empiriquement, en observant la distance moyenne des points au centre de leur cluster pour différentes valeurs de $k$.

# Algorithme

Pour choisir le nombre de clusters d'un [[k-means]], on considère la distance moyenne au centroïde, la moyenne, sur les $N$ points, de la distance entre un point $x_i$ et le centre $c_{f(i)}$ de son cluster :

$$\frac{1}{N} \sum_{i=1}^{N} d(x_i, c_{f(i)})$$

où $d$ désigne la [[Mesures de similarité et de distance|distance]] utilisée. On procède alors empiriquement :

1. essayer différentes valeurs de $k$ ;
2. pour chaque valeur, calculer cette distance moyenne ;
3. observer son évolution quand $k$ augmente : elle chute rapidement jusqu'à la bonne valeur de $k$, puis ne varie plus que faiblement ;
4. retenir cette valeur de $k$, au niveau du coude de la courbe.

# Remarque

Voir aussi la [[Qualité d'un clustering|qualité d'un clustering]].

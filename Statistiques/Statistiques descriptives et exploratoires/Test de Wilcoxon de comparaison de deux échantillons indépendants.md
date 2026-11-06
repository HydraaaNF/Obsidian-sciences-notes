# Définition

Le **test de Wilcoxon de comparaison de deux échantillons indépendants** répond à la question suivante : deux échantillons indépendants, de tailles respectives $n$ et $m$, proviennent-ils de la même population, c'est-à-dire de la même loi ?

L'[[Hypothèse nulle et hypothèse alternative|hypothèse nulle]] $H_0$ postule que les deux échantillons sont issus d'une même loi ; l'hypothèse alternative $H_1$ postule que les deux lois diffèrent.

On dispose des observations $\{x_1, \dots, x_n\}$ et $\{y_1, \dots, y_m\}$, et l'on compare les deux échantillons par les rangs que prennent leurs valeurs une fois réunies.

La [[Statistique de test|statistique de test]] est

$$U = \#\{(x_i, y_j) \mid x_i > y_j\}$$

c'est-à-dire le nombre de paires formées d'une valeur du premier échantillon et d'une valeur du second, la première étant strictement supérieure à la seconde.

# Algorithme

1. réunir toutes les valeurs $x_i$ et $y_j$ et les trier par ordre croissant ;
2. compter les paires $(x_i, y_j)$ vérifiant $x_i > y_j$ : leur nombre est la valeur observée de $U$ ;
3. confronter cette valeur à la région critique du test.

# Propriétés

La statistique $U$ est un nombre entier compris entre $0$ et $nm$, les deux bornes correspondant aux classements les plus tranchés.

$U = 0$ lorsque tous les $x_i$ sont inférieurs aux $y_j$ : le classement croissant range d'abord $x_1, \dots, x_n$, puis $y_1, \dots, y_m$.

$U = nm$ lorsque tous les $y_j$ sont inférieurs aux $x_i$ : le classement croissant range d'abord $y_1, \dots, y_m$, puis $x_1, \dots, x_n$.

Sous $H_0$, $U$ suit asymptotiquement la loi

$$\mathcal{N}\left(\frac{nm}{2}, \sqrt{\frac{nm(n+m+1)}{12}}\right)$$

La [[Zone critique et seuil d'un test|région critique]] est

$$\left|U - \frac{nm}{2}\right| > k_\alpha$$

où $k_\alpha$ est le seuil fixé par le [[Risque de première espèce|risque de première espèce]] $\alpha$.

# Interprétation

Sous $H_0$, le classement des $n + m$ valeurs doit être homogène : les rangs se répartissent sans tendance entre les deux échantillons, et $U$ fluctue autour de sa valeur centrale $\frac{nm}{2}$.

Un $U$ proche de $0$ ou de $nm$ traduit au contraire deux échantillons nettement séparés : toutes les valeurs de l'un se situent du même côté de celles de l'autre. Plus $U$ s'éloigne de $\frac{nm}{2}$, moins l'hypothèse d'une loi commune est crédible.

# Remarque

Le test ne suppose aucune forme particulière pour la loi des échantillons : il fonctionne dans le cas général, là où l'égalité des moyennes de deux populations gaussiennes se teste par le [[Test de Student d'égalité de deux moyennes|test de Student]]. Il constitue de ce fait une alternative non paramétrique à ce dernier.

Le second paramètre de la loi asymptotique est l'écart-type de $U$ ; la variance vaut donc $\frac{nm(n+m+1)}{12}$, et c'est elle qui intervient dans le calcul des probabilités associées à la [[Loi gaussienne|loi gaussienne]] limite.

La région critique écrite avec une valeur absolue est bilatérale : on rejette $H_0$ dès que $U$ s'écarte de $\frac{nm}{2}$ d'un côté comme de l'autre, ce qui correspond à une hypothèse alternative de lois différentes, sans direction privilégiée.

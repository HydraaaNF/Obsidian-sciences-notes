# Définition

Le **test du chi-deux d'homogénéité** compare plusieurs sous-échantillons d'un même ensemble au regard d'un caractère qualitatif à $r$ modalités : il teste l'hypothèse que tous ces sous-échantillons sont issus d'une même [[Population statistique et caractère|population]], autrement dit que la distribution des modalités y est identique.

Les effectifs observés se rangent dans un [[Tableau de contingence]] à $k$ lignes (les sous-échantillons) et $r$ colonnes (les modalités) :

| | Modalité 1 | Modalité 2 | $\cdots$ | Modalité $r$ | Total |
| :--- | :---: | :---: | :---: | :---: | :---: |
| Sous-échantillon 1 | $n_{11}$ | $n_{12}$ | $\cdots$ | $n_{1r}$ | $n_{1\cdot}$ |
| Sous-échantillon 2 | $n_{21}$ | $n_{22}$ | $\cdots$ | $n_{2r}$ | $n_{2\cdot}$ |
| $\vdots$ | $\vdots$ | $\vdots$ | $\ddots$ | $\vdots$ | $\vdots$ |
| Sous-échantillon $k$ | $n_{k1}$ | $n_{k2}$ | $\cdots$ | $n_{kr}$ | $n_{k\cdot}$ |
| Total | $n_{\cdot 1}$ | $n_{\cdot 2}$ | $\cdots$ | $n_{\cdot r}$ | $n$ |

où $n_{ij}$ est l'effectif de la modalité $j$ dans le sous-échantillon $i$, $n_{i\cdot}$ le total de la ligne $i$, $n_{\cdot j}$ le total de la colonne $j$ et $n$ l'effectif total.

La statistique du test s'écrit, en fonction des probabilités $p_j$ des modalités sous l'hypothèse nulle,

$$D^2 = \sum_{i} \sum_{j} \frac{(n_{ij} - n_{i\cdot} p_j)^2}{n_{i\cdot} p_j}$$

et, les $p_j$ étant estimées par les fréquences globales $n_{\cdot j} / n$,

$$D^2 = \sum_{i} \sum_{j} \frac{\left(n_{ij} - \frac{n_{i\cdot} n_{\cdot j}}{n}\right)^2}{\frac{n_{i\cdot} n_{\cdot j}}{n}}$$

Sous l'hypothèse nulle $H_0$ selon laquelle tous les sous-échantillons suivent la même loi, cette statistique suit asymptotiquement une [[Loi du chi-deux]] à $(k-1)(r-1)$ degrés de liberté :

$$D^2 \rightsquigarrow \chi^2_{(k-1)(r-1)}$$

# Interprétation

Chaque terme de la somme compare l'effectif observé $n_{ij}$ à l'effectif attendu si le sous-échantillon $i$ suivait la répartition globale des modalités, $n_{i\cdot} n_{\cdot j} / n$. La statistique $D^2$ mesure ainsi l'écart d'ensemble entre les profils des $k$ sous-échantillons : elle s'annule lorsque chacun reproduit exactement la répartition globale, et croît avec l'hétérogénéité des sous-échantillons entre eux.

# Remarque

La statistique $D^2$ est la même que celle du [[Test du chi-deux d'indépendance]] et du [[Test d'ajustement du chi-deux|test d'ajustement du chi-deux]], et sa loi sous l'hypothèse nulle également. La différence porte sur l'hypothèse d'échantillonnage testée : l'indépendance concerne deux caractères observés sur une même population, tandis que l'homogénéité concerne plusieurs sous-échantillons d'un même ensemble dont on teste l'identité de loi. C'est le protocole de collecte des données qui distingue les deux situations, non le calcul.

Le rejet de $H_0$ s'interprète comme une différence significative entre les distributions des sous-échantillons, sans préciser lequel s'écarte des autres.

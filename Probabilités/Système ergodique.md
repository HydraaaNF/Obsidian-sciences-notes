# Définition

Un [[File d'attente|système d'attente]] est dit **ergodique** lorsqu'il existe une distribution limite $\pi$ indépendante des conditions initiales :

$$\pi_j = \lim_{t \rightarrow +\infty} \mathbb{P}(N(t) = j)$$

où $N(t)$ désigne le nombre de clients présents dans la file à l'instant $t$.

On peut alors introduire une [[Variable aléatoire|variable aléatoire]] $N_\infty$ représentant le nombre de clients à un instant quelconque du régime stationnaire : la distribution $\pi$ est la [[Loi d'une variable aléatoire|loi de probabilité]] de $N_\infty$.

On appelle $R_n$ le temps que passe le $n$-ième client dans le système (son temps d'attente plus son temps de service), et on pose

$$\bar{R} = \lim_{n \rightarrow +\infty} \frac{1}{n} \sum_{i=1}^n R_i$$

$$\bar{\lambda} = \lim_{t \rightarrow +\infty} \frac{A(t)}{t}$$

où $A(t)$ est le nombre d'arrivées de clients dans l'intervalle de temps $]0, t]$.

# Interprétation

- $\bar{R}$ représente le temps moyen passé dans la file par un client quelconque en régime stationnaire.
- $\bar{\lambda}$ est le taux moyen des arrivées, c'est-à-dire le nombre moyen d'arrivées par unité de temps en régime stationnaire.
- La distribution limite $\pi$ est l'objet central de l'étude : elle peut fournir plusieurs paramètres intéressants en ingénierie.

# Remarque

- L'ergodicité est l'hypothèse sous laquelle s'applique la [[Formule de Little]].
- Voir [[Chaîne de Markov à temps continu]] pour l'étude du régime stationnaire des files markoviennes.

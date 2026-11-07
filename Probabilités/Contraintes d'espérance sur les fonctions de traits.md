#adm-8

# Définition

Soit $x$ une variable prenant ses valeurs dans $\{x_1, \ldots, x_n\}$. Les contraintes qui pèsent sur sa distribution s'expriment au moyen de $m$ fonctions de traits mesurables $f_k(x)$, dont l'espérance théorique doit coïncider avec les faits connus, par exemple les fréquences empiriques observées. Chaque contrainte s'écrit, pour $k = 1, \ldots, m$ :

$$\sum_{i=1}^{n} f_k(x_i)\,\mathbb{P}(x_i) = F_k$$

où $F_k$ est la valeur du fait observé associé à la fonction de trait $f_k$.

# Interprétation

Une contrainte d'espérance fixe une moyenne pondérée de la fonction de trait $f_k$ sous la distribution recherchée : la loi $\mathbb{P}$ doit donner à $f_k$ la même espérance que celle mesurée sur les faits. Le fait empirique se transforme ainsi en une égalité portant directement sur la distribution, ce qui le rend utilisable comme contrainte de modélisation : parmi les distributions qui vérifient les $m$ contraintes, on retient celle d'[[Entropie d'une variable aléatoire discrète|entropie]] maximale, conformément au [[Principe du maximum d'entropie]].

# Remarque

- La variable $x$ dont on cherche la distribution ne doit pas être confondue avec les données d'entraînement : ses valeurs $x_1, \ldots, x_n$ sont les issues possibles du phénomène modélisé, pas les observations recueillies.
- Lorsque le fait connu est une fréquence empirique, le membre de droite $F_k$ est l'[[Espérance empirique d'une fonction de trait|espérance empirique]] de la fonction de trait sur les données.
- Les paramètres de la distribution de maximum d'entropie sous ces contraintes sont déterminés de façon à les vérifier exactement ; leur calcul est décrit dans [[Estimation des paramètres par les multiplicateurs de Lagrange]] et la forme obtenue dans [[Forme exponentielle d'une distribution de maximum d'entropie]].
- Un jeu concret de fonctions de traits et les contraintes qu'il induit sur une distribution de traduction sont détaillés dans [[Fonctions de traits d'un exemple de traduction]] et [[Distribution de maximum d'entropie d'une traduction]].

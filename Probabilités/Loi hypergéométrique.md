# Définition

On considère un lot de $n$ composants dont $d$ sont défectueux, et l'on prélève **sans remise** $m$ composants. La loi hypergéométrique est la loi du nombre $X$ de composants défectueux dans le prélèvement.

La probabilité que le prélèvement contienne exactement $k$ composants défectueux vaut

$$\mathbb{P}(X = k) = \frac{\binom{d}{k}\binom{n-d}{m-k}}{\binom{n}{m}}, \qquad \max(0,\, m - (n-d)) \le k \le \min(m,\, d).$$

C'est une loi de [[Variable aléatoire discrète|variable aléatoire discrète]] : $X$ ne peut prendre qu'un nombre fini de valeurs entières. Le dénombrement s'effectue avec des [[Combinaison|combinaisons]] : au numérateur, $\binom{d}{k}$ compte les choix des $k$ composants défectueux parmi les $d$ du lot et $\binom{n-d}{m-k}$ les choix des $m-k$ composants non défectueux parmi les $n-d$ du lot ; au dénominateur, $\binom{n}{m}$ est le nombre total de prélèvements possibles de $m$ composants parmi les $n$.

# Interprétation

Le prélèvement étant effectué sans remise, la composition du lot change à chaque tirage : la probabilité qu'un composant prélevé soit défectueux dépend des composants déjà prélevés, et les tirages ne sont pas indépendants.

# Propriétés

Son [[Espérance d'une variable aléatoire|espérance]] vaut

$$\mathbb{E}(X) = m\,\frac{d}{n}.$$

# Liens avec d'autres lois

- La loi hypergéométrique se distingue de la [[Loi binomiale|loi binomiale]] : la loi binomiale compte le nombre de succès sur un nombre fixé d'épreuves indépendantes de même probabilité de succès $p$ (tirage avec remise), tandis que la loi hypergéométrique correspond à un tirage sans remise dans une population finie.
- La loi hypergéométrique est la loi de la somme de $m$ variables de [[Loi de Bernoulli|Bernoulli]] de paramètre $d/n$, échangeables mais non [[Indépendance de variables aléatoires|indépendantes]].
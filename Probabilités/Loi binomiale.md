# Définition

La loi binomiale est la loi du nombre de réalisations d'un événement de probabilité d'occurrence $p$ au cours de $n$ épreuves de Bernoulli indépendantes. On note $X \sim \mathcal{B}(n, p)$ lorsque $X$ est la somme de $n$ [[Loi de Bernoulli|variables de Bernoulli]] indépendantes.

Sa fonction de masse est donnée par

$$\mathbb{P}[X = k] = C_n^k\, p^k (1-p)^{n-k}, \qquad k \in \{0, 1, \ldots, n\},$$

où $C_n^k$ désigne le nombre de [[Combinaison|combinaisons]] de $k$ éléments parmi $n$.

# Propriétés

Son [[Espérance d'une variable aléatoire|espérance]] et sa [[Variance|variance]] valent

- $\mathbb{E}[X] = np$ ;
- $\mathbb{V}[X] = np(1-p)$.

Sa [[Fonction génératrice|fonction génératrice]] vaut

$$G_X(z) = \mathbb{E}(z^X) = (pz + 1-p)^n.$$

# Liens avec d'autres lois

- La [[Loi de Bernoulli|loi de Bernoulli]] est le cas particulier $n = 1$ de la loi binomiale, c'est-à-dire la loi de la somme d'une seule variable de Bernoulli indépendante.
- Pour $p$ petit et $n$ grand ($n \geq 20$, $p \leq 0.05$), la loi binomiale est approchée par la [[Loi de Poisson|loi de Poisson]] de paramètre $\alpha = np$.
- La somme de deux variables aléatoires [[Indépendance de variables aléatoires|indépendantes]] de lois binomiales de même paramètre $p$ suit une loi binomiale : si $X \sim \mathcal{B}(n, p)$ et $Y \sim \mathcal{B}(m, p)$, alors $X + Y \sim \mathcal{B}(n + m, p)$.
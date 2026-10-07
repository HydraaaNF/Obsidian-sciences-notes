# Définition

La loi binomiale négative est la loi du nombre d'épreuves de [[Loi de Bernoulli|Bernoulli]] nécessaires pour obtenir le $r$-ième succès. C'est une loi de probabilité [[Probabilité discrète|discrète]], à valeurs dans $\{r, r + 1, r + 2, \ldots\}$.

Convention de comptage retenue : $X$ désigne le nombre total d'épreuves effectuées, la dernière étant celle du $r$-ième succès, donc $X \geq r$. D'autres conventions existent, qui comptent plutôt le nombre d'échecs précédant le $r$-ième succès.

Pour une suite d'épreuves de Bernoulli indépendantes et de même probabilité de succès $p \in \, ]0, 1]$ et pour un entier $r \geq 1$, la fonction de masse de $X \sim \mathcal{BN}(r, p)$ est donnée par

$$\mathbb{P}(X = n) = \binom{n-1}{r-1} p^r (1-p)^{n-r}, \qquad n \geq r.$$

# Propriétés

Son [[Espérance d'une variable aléatoire|espérance]] et sa [[Variance|variance]] valent

$$\mathbb{E}(X) = \frac{r}{p}$$

$$\mathbb{V}(X) = \frac{r(1-p)}{p^2}.$$

Sa [[Fonction génératrice|fonction génératrice]] vaut

$$G_X(z) = \mathbb{E}(z^X) = \left(\frac{pz}{1-(1-p)z}\right)^r, \qquad |z| \leq 1.$$

# Interprétation

La loi binomiale négative modélise un temps d'attente : le nombre d'épreuves nécessaires, dans un processus de Bernoulli de paramètre $p$, pour observer $r$ succès.

# Remarque

Elle se distingue de la [[Loi binomiale|loi binomiale]], qui compte le nombre de succès obtenus sur un nombre fixé d'épreuves indépendantes.

# Liens avec d'autres lois

- La [[Loi géométrique|loi géométrique]] est le cas particulier $r = 1$ : elle décrit le nombre d'épreuves nécessaires pour obtenir le premier succès.
- La loi binomiale négative de paramètres $r$ et $p$ est la loi de la somme de $r$ variables aléatoires [[Loi géométrique|géométriques]] indépendantes de paramètre $p$.
- La somme de deux variables aléatoires [[Indépendance de variables aléatoires|indépendantes]] de lois binomiales négatives de même paramètre $p$ suit une loi binomiale négative : si $X \sim \mathcal{BN}(r, p)$ et $Y \sim \mathcal{BN}(s, p)$, alors $X + Y \sim \mathcal{BN}(r + s, p)$.
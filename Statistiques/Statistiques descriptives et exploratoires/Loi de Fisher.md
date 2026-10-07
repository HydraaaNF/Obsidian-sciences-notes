# Définition

Soient $U$ et $V$ deux [[Variable aléatoire réelle|variables aléatoires réelles]] [[Indépendance de variables aléatoires|indépendantes]], de lois respectives $\chi_p^2$ et $\chi_q^2$ ([[Loi du chi-deux|lois du chi-deux]] à $p$ et $q$ degrés de liberté). La variable aléatoire définie par

$$\frac{U/p}{V/q}$$

suit une **loi de Fisher** $\mathcal{F}(p,q)$.

# Interprétation

La loi de Fisher intervient dans le [[Test de Fisher d'égalité de variances|test de Fisher d'égalité de variances]], qui teste l'égalité des variances des lois mères [[Loi gaussienne|gaussiennes]] de deux [[Échantillon et échantillonnage|échantillons]] indépendants, au moyen de leurs [[Variance empirique|variances empiriques]].

# Propriétés

Si $F \sim \mathcal{F}(p, q)$, son [[Espérance d'une variable aléatoire|espérance]] et sa [[Variance|variance]] valent

$$\mathbb{E}(F) = \frac{q}{q-2} \quad \text{pour } q > 2$$

$$\mathbb{V}(F) = \frac{2q^2(p+q-2)}{p(q-2)^2(q-4)} \quad \text{pour } q > 4.$$

# Liens avec d'autres lois

- La loi de Fisher est stable par inversion : si $F \sim \mathcal{F}(p, q)$, alors $1/F \sim \mathcal{F}(q, p)$.
- La loi $\mathcal{F}(1, n)$ est la loi du carré d'une variable aléatoire de [[Loi de Student|loi de Student]] à $n$ degrés de liberté.
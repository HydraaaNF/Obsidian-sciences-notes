#adm-0bis #adm-9

# Loi

La **loi du chi-deux** à $n$ degrés de liberté, notée $\chi_n^2$, est la loi de la variable aléatoire

$$ Y = X_1^2 + \dots + X_n^2, $$

où $X_1, \dots, X_n$ sont des variables aléatoires indépendantes et identiquement distribuées de [[Loi gaussienne|loi normale centrée réduite]] $\mathcal{N}(0,1)$.

Sa densité de probabilité s'écrit, pour $x > 0$,

$$f(x) = \frac{1}{2^{\frac{n}{2}} \Gamma\left(\frac{n}{2}\right)} x^{\frac{n}{2} - 1} e^{-\frac{x}{2}},$$

où $\Gamma$ désigne la [[Fonction Gamma|fonction Gamma]] ; elle est nulle pour $x \leq 0$.

# Propriétés

La loi du chi-deux à $n$ degrés de liberté est également une [[Loi gamma|loi Gamma]] $\Gamma\left(\frac{n}{2}, \frac{1}{2}\right)$. Son [[Espérance d'une variable aléatoire|espérance]] et sa [[Variance|variance]] valent alors

$$\mathbb{E}[Y] = n$$

$$\mathbb{V}(Y) = 2n.$$

La somme de deux variables aléatoires indépendantes distribuées respectivement selon une loi $\chi_p^2$ et une loi $\chi_q^2$ suit une loi $\chi_{p+q}^2$.

Sa [[Fonction caractéristique|fonction caractéristique]] vaut

$$\Phi_Y(\xi) = (1 - 2i\xi)^{-n/2}.$$

Les quantiles de la loi sont tabulés pour les degrés de liberté de 1 à 13. La probabilité portée en tête de colonne est la probabilité de dépassement : la valeur $\chi^2_p$ vérifie $\mathbb{P}[Y > \chi^2_p] = p$.

| Degrés de liberté | $\chi^2_{0{,}9995}$ | $\chi^2_{0{,}999}$ | $\chi^2_{0{,}995}$ | $\chi^2_{0{,}990}$ | $\chi^2_{0{,}975}$ | $\chi^2_{0{,}95}$ | $\chi^2_{0{,}90}$ | $\chi^2_{0{,}85}$ | $\chi^2_{0{,}80}$ |
|---|---|---|---|---|---|---|---|---|---|
| 1 | 0,000 | 0,000 | 0,000 | 0,000 | 0,001 | 0,004 | 0,016 | 0,036 | 0,064 |
| 2 | 0,001 | 0,002 | 0,010 | 0,020 | 0,051 | 0,103 | 0,211 | 0,325 | 0,446 |
| 3 | 0,015 | 0,024 | 0,072 | 0,115 | 0,216 | 0,352 | 0,584 | 0,798 | 1,005 |
| 4 | 0,064 | 0,091 | 0,207 | 0,297 | 0,484 | 0,711 | 1,064 | 1,366 | 1,649 |
| 5 | 0,158 | 0,210 | 0,412 | 0,554 | 0,831 | 1,145 | 1,610 | 1,994 | 2,343 |
| 6 | 0,299 | 0,381 | 0,676 | 0,872 | 1,237 | 1,635 | 2,204 | 2,661 | 3,070 |
| 7 | 0,485 | 0,598 | 0,989 | 1,239 | 1,690 | 2,167 | 2,833 | 3,358 | 3,822 |
| 8 | 0,710 | 0,857 | 1,344 | 1,646 | 2,180 | 2,733 | 3,490 | 4,078 | 4,594 |
| 9 | 0,972 | 1,152 | 1,735 | 2,088 | 2,700 | 3,325 | 4,168 | 4,817 | 5,380 |
| 10 | 1,265 | 1,479 | 2,156 | 2,558 | 3,247 | 3,940 | 4,865 | 5,570 | 6,179 |
| 11 | 1,587 | 1,834 | 2,603 | 3,053 | 3,816 | 4,575 | 5,578 | 6,336 | 6,989 |
| 12 | 1,934 | 2,214 | 3,074 | 3,571 | 4,404 | 5,226 | 6,304 | 7,114 | 7,807 |
| 13 | 2,305 | 2,617 | 3,565 | 4,107 | 5,009 | 5,892 | 7,042 | 7,901 | 8,634 |

La lecture croise la ligne du nombre de degrés de liberté et la colonne de la probabilité voulue : pour $n = 5$ et $p = 0{,}95$, la table donne $\chi^2_{0{,}95} = 1{,}145$. La lecture à double entrée de ces tables est décrite dans [[Lecture d'une table de probabilité]].

# Interprétation

La loi du chi-deux est la loi d'une somme de carrés d'écarts standardisés : elle s'annule quand tous les écarts sont nuls et croît avec leur amplitude. C'est ce qui en fait la loi de référence des statistiques mesurant un écart à un modèle, comme celles du [[Test d'ajustement du chi-deux|test d'ajustement du chi-deux]] et du [[Test du chi-deux d'homogénéité de plusieurs sous-échantillons|test du chi-deux d'homogénéité de plusieurs sous-échantillons]] : plus la valeur observée de la statistique dépasse le quantile tabulé, plus l'écart au modèle est improbable.

Le nombre de degrés de liberté fixe l'allure de la loi : l'espérance croît comme $n$ et l'écart-type comme $\sqrt{2n}$, si bien que la dispersion relative autour de la moyenne diminue quand $n$ augmente.

# Liens avec d'autres lois

Pour un échantillon gaussien de variance $\sigma^2$, la statistique $\frac{(n-1)S'^2}{\sigma^2}$ suit une loi du chi-deux à $n-1$ degrés de liberté : voir [[Loi de la variance empirique corrigée|loi de la variance empirique corrigée]].

La [[Loi de Student|loi de Student]] est le quotient d'une variable de loi normale centrée réduite par la racine d'une variable du chi-deux divisée par ses degrés de liberté. Le quotient de deux variables du chi-deux indépendantes, chacune divisée par son nombre de degrés de liberté, suit une [[Loi de Fisher|loi de Fisher]] :

$$\frac{U/p}{V/q} \sim \mathcal{F}(p, q) \quad \text{pour } U \sim \chi_p^2 \text{ et } V \sim \chi_q^2 \text{ indépendantes}.$$

La loi intervient encore dans le [[Test d'ajustement du chi-deux|test d'ajustement du chi-deux]], le [[Test du chi-deux d'indépendance|test du chi-deux d'indépendance]] et le [[Test du chi-deux d'homogénéité de plusieurs sous-échantillons|test du chi-deux d'homogénéité de plusieurs sous-échantillons]].

# Définition

La loi uniforme discrète est la loi d'une [[Variable aléatoire discrète]] prenant un nombre fini $n$ de valeurs possibles $x_1, \ldots, x_n$, toutes de même probabilité :

$$p_X(x_i) = \mathbb{P}[X = x_i] = \frac{1}{n}, \qquad i = 1, \ldots, n.$$

# Interprétation

C'est la distribution a priori lorsque rien n'est connu : en l'absence d'information sur $X$, aucune de ses valeurs possibles n'est privilégiée.

# Propriétés

Pour $X$ uniforme discrète sur $\{1, \dots, n\}$, son [[Espérance d'une variable aléatoire|espérance]] et sa [[Variance|variance]] valent

$$\mathbb{E}(X) = \frac{n+1}{2}$$

$$\mathbb{V}(X) = \frac{n^2-1}{12},$$

et sa [[Fonction génératrice|fonction génératrice]] vaut

$$G_X(z) = \frac{z(z^n-1)}{n(z-1)}.$$

# Liens avec d'autres lois

- La loi uniforme discrète est un cas particulier de la [[Probabilité discrète]] : son support ne comporte qu'un nombre fini de valeurs.
- La [[Loi de Bernoulli]] de paramètre $p = \frac{1}{2}$ correspond au cas $n = 2$ : elle prend deux valeurs, chacune de probabilité $\frac{1}{2}$.
- La [[Loi uniforme continue]] est son analogue continu.
- Si $U$ suit la [[Loi uniforme continue|loi uniforme continue]] sur $[0, 1]$, alors $\lfloor nU \rfloor + 1$ suit la loi uniforme discrète sur $\{1, \dots, n\}$.

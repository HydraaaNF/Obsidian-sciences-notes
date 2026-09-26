# Définition
Trois indicateurs pour juger la qualité d'une [[Analyse en composantes principales|ACP]] :

- **fraction d'inertie retenue** (mesure globale) : $\dfrac{\lambda_1 + \ldots + \lambda_q}{I_g}$
- **angle entre le plan principal et un individu** (mesure locale) : un angle petit indique une bonne représentation
- **erreur de reconstruction** pour un individu (mesure locale) : $\|x_i - \bar{U}\bar{U}^Tx_i\|$

# Interprétation
La mesure globale évalue la qualité de la projection dans son ensemble ; les mesures locales évaluent la qualité de représentation individu par individu.

# Exemple
Valeurs propres obtenues sur un jeu de données réel (Saporta 2002, pp. 180-183) :

| $\lambda$ | 6,21 | 0,89 | 0,42 | 0,32 | 0,14 | 0,01 | 0,005 |
|---|---|---|---|---|---|---|---|
| Inertie (%) | 77,57 | 11,21 | 5,26 | 3,99 | 1,74 | 0,11 | 0,06 |
| Cumulée (%) | 77,57 | 88,78 | 94,04 | 98,0 | 99,8 | 99,9 | 100 |

Avec seulement les 2 premières composantes, on retient déjà 88,78 % de l'inertie totale — illustration concrète de la fraction d'inertie retenue comme mesure de qualité globale.

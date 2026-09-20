# Définition
Trois indicateurs pour juger la qualité d'une [[Analyse en composantes principales|ACP]] :

- **fraction d'inertie retenue** (mesure globale) : $\dfrac{\lambda_1 + \ldots + \lambda_q}{I_g}$
- **angle entre le plan principal et un individu** (mesure locale) : un angle petit indique une bonne représentation
- **erreur de reconstruction** pour un individu (mesure locale) : $\|x_i - \bar{U}\bar{U}^Tx_i\|$

# Interprétation
La mesure globale évalue la qualité de la projection dans son ensemble ; les mesures locales évaluent la qualité de représentation individu par individu.

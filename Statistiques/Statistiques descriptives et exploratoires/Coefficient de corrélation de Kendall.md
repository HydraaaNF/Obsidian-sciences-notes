# Définition
Pour toutes les paires $(x_i, y_i)$ et $(x_j, y_j)$, on regarde le signe de $(x_i - x_j)(y_i - y_j)$ :
- $+1$ si les deux paires sont dans le même ordre ($x_i < x_j$ et $y_i < y_j$)
- $-1$ sinon

Le coefficient $\tau$ de Kendall est
$$\tau_{XY} = \frac{2S}{n(n-1)}$$
où $S$ est la somme des signes sur toutes les paires.

# Interprétation
Mesure si $X$ et $Y$ varient dans le même sens, en comptant la proportion de paires concordantes vs discordantes. Comme [[Coefficient de corrélation de Spearman|Spearman]], détecte les dépendances monotones non linéaires.

# Exemple
Sur le même jeu de données que l'exemple de [[Coefficient de corrélation de Spearman]] (10 vins classés par deux experts), on obtient $\tau_{XY} = 0{,}64$.

# Remarque
$\tau$ est presque systématiquement plus faible que $\rho$ de Spearman sur un même jeu de données — c'est une propriété générale des deux coefficients, pas une particularité de cet exemple : $\tau$ compte des paires concordantes/discordantes tandis que $\rho$ travaille sur l'écart des rangs, une mesure plus sensible aux grands écarts.

# Définition

Soit $(X_n)_{n \in \mathbb{N}}$ une suite de [[Variable aléatoire réelle|variables aléatoires réelles]] et $X$ une variable aléatoire réelle, définies sur un même [[Espace probabilisé|espace probabilisé]]. On dit que la suite $(X_n)_{n \in \mathbb{N}}$ converge presque sûrement vers $X$ si

$$\mathbb{P}\left[\left\{\omega \in \Omega \mid \lim_{n \to +\infty} X_n(\omega) = X(\omega)\right\}\right] = 1.$$

On note alors $X_n \xrightarrow{p.s.} X$.

# Interprétation

Cela signifie que si l'on observe une trajectoire $(X_n(\omega))_{n \in \mathbb{N}}$ (les valeurs prises par la suite lors d'une expérience aléatoire $\omega \in \Omega$) ainsi que la valeur $X(\omega)$ pour cette expérience, on observera que la suite de réels $(X_n(\omega))_{n \in \mathbb{N}}$ converge vers $X(\omega)$, sauf cas exceptionnel : les expériences $\omega$ pour lesquelles on n'a pas cette convergence forment un évènement de probabilité nulle.

# Théorème

Sous les hypothèses de la définition précédente (résultat admis), si $X_n \xrightarrow{p.s.} X$ alors $X_n \xrightarrow{\mathbb{P}} X$ : la suite $(X_n)_{n \in \mathbb{N}}$ [[Convergence en probabilité|converge en probabilité]] vers $X$.

Ainsi, la convergence presque sûre est une propriété plus forte que la convergence en probabilité.

# Remarque

La convergence presque sûre est souvent appelée « convergence forte », et la convergence en probabilité « convergence faible », notamment dans les énoncés des [[Loi forte des grands nombres|lois des grands nombres]].

En pratique, vérifier directement la définition de la convergence presque sûre n'est pas aisé : on utilise plutôt la condition suffisante fournie par le [[Critère de Borel-Cantelli]].

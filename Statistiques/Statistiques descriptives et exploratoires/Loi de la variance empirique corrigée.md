# Théorème

Soit $X_1, \dots, X_n$ des variables aléatoires indépendantes et identiquement distribuées (i.i.d.) [[Loi gaussienne|gaussiennes]] de [[Variance|variance]] $\sigma^2$. On note $\overline{X} = \frac{1}{n} \sum_{i=1}^{n} X_i$ leur [[Moyenne empirique|moyenne empirique]], $S^2$ la [[Variance empirique|variance empirique]] et $S'^2$ la variance empirique corrigée :

$$S^2 = \frac{1}{n} \sum_{i=1}^{n} (X_i - \overline{X})^2$$

$$S'^2 = \frac{1}{n-1} \sum_{i=1}^{n} (X_i - \overline{X})^2$$

Alors

$$\frac{nS^2}{\sigma^2} = \frac{(n-1)S'^2}{\sigma^2} = \sum_{i=1}^{n} \left( \frac{X_i - \overline{X}}{\sigma} \right)^2 \quad \text{suit une loi } \chi_{n-1}^2$$

où $\chi_{n-1}^2$ désigne la [[Loi du chi-deux|loi du chi-deux]] à $n-1$ degrés de liberté.

# Propriétés

Les variables $\frac{X_i - \overline{X}}{\sigma}$, pour $1 \leq i \leq n$, ne sont pas indépendantes : pour $i \neq j$, leur [[Covariance|covariance]] vaut

$$\begin{aligned} \operatorname{cov}\left(X_i - \overline{X}, X_j - \overline{X}\right) &= \operatorname{cov}\left(X_i, X_j\right) - 2\operatorname{cov}\left(\overline{X}, X_j\right) + \mathbb{V}\left(\overline{X}\right) \\ &= -2\operatorname{cov}\left(\overline{X}, X_j\right) + \mathbb{V}\left(\overline{X}\right) \\ &= -2\frac{\sigma^2}{n} + \frac{\sigma^2}{n} \\ &= -\frac{\sigma^2}{n} . \end{aligned}$$

# Remarque

D'après la définition d'une loi du $\chi_n^2$, l'[[Estimateur du maximum de vraisemblance|estimateur du maximum de vraisemblance]] de $\sigma^2$,

$$\widehat{\sigma^2} = \frac{1}{n} \sum_{i=1}^{n} (X_i - \mathbb{E}[X])^2 ,$$

vérifie

$$\frac{n\widehat{\sigma^2}}{\sigma^2} = \sum_{i=1}^{n} \left( \frac{X_i - \mathbb{E}[X]}{\sigma} \right)^2 \sim \chi_n^2 ,$$

étant donné que cela correspond à la somme de $n$ carrés de variables aléatoires gaussiennes centrées réduites indépendantes. Le fait de remplacer $\mathbb{E}[X]$ par $\overline{X}$ « impose » une dépendance entre toutes les variables $\frac{X_i - \overline{X}}{\sigma}$ pour $1 \leq i \leq n$, justifiant intuitivement la perte d'un degré de liberté dans la loi du chi-deux.

La statistique $\frac{(n-1)S'^2}{\sigma^2}$ sert à construire un [[Intervalle de confiance d'une variance|intervalle de confiance pour la variance]] $\sigma^2$.

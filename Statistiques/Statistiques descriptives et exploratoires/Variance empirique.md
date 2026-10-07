# Définition

La **variance empirique** d'un ensemble d'observations $X_1, \ldots, X_n$ est l'[[Estimateur|estimateur]] de la [[Variance]] donné par

$$S^2 = \frac{1}{n} \sum_{i=1}^n (X_i - \overline{X})^2$$

où $\overline{X} = \frac{1}{n} \sum_{i=1}^n X_i$ est la [[Moyenne empirique|moyenne empirique]] de l'ensemble. Pour une série d'observations $x_1, \dots, x_n$ de moyenne $\bar{x}$, elle s'écrit

$$s^2 = \frac{1}{n}\sum_{i=1}^{n} (x_i - \bar{x})^2.$$

Elle s'écrit aussi

- $S^2 = \frac{\sum X_i^2}{n} - \overline{X}^2$ ;
- $S^2 = \frac{\sum (X_i - m)^2}{n} - (\overline{X} - m)^2$,

où $m$ est la moyenne de la population.

# Propriétés

L'[[Espérance d'une variable aléatoire|espérance]] de la variance empirique vaut

$$\mathbb{E}[S^2] = \frac{n - 1}{n} \sigma^2$$

où $\sigma^2$ est la variance de la population. L'estimateur est donc [[Biais d'un estimateur|biaisé]], puisque $\mathbb{E}[S^2] \neq \sigma^2$, mais il converge vers $\sigma^2$ lorsque $n \to \infty$.

# Remarque

La version corrigée de la variance empirique, qui divise par $n - 1$ plutôt que par $n$, est un estimateur sans biais de la [[Variance]] :

$$S'^2 = \frac{1}{n-1} \sum_{i=1}^n (X_i - \overline{X})^2 = \frac{1}{n-1}\sum_{i=1}^{n} (x_i - \bar{x})^2.$$

La [[Loi de la variance empirique corrigée]] en décrit la loi ; pour la loi de $\overline{X}$, voir [[Distribution de la moyenne empirique]]. Ne pas confondre la variance empirique avec la [[Moment centré d'ordre k|variance théorique]] $\mathbb{V}(X)$ d'une variable aléatoire.

# Définition

On considère un ensemble de mesures $x_1, \dots, x_n$ issues d'une [[Loi gaussienne|loi gaussienne]] de moyenne $\mathbb{E}[X] = m$ et de [[Variance|variance]] $\sigma^2$ inconnues. On souhaite, à partir de ces mesures, obtenir une estimation de $m$ et un [[Intervalle de confiance|intervalle de confiance]] pour cette estimation.

Comme dans le cas d'une variance connue, on considère l'[[Estimateur|estimateur]] $\overline{X}$ de $m$, la [[Moyenne empirique|moyenne empirique]] : l'intervalle de confiance construit [[Intervalle de confiance de la moyenne d'une loi normale de variance connue|lorsque la variance est connue]] reste valable, bien qu'inutilisable, puisque $\sigma$ est inconnu. Plus précisément, la fonction

$$g(\overline{X}) = \frac{\overline{X} - m}{\sqrt{\frac{\sigma^2}{n}}} \sim \mathcal{N}(0, 1)$$

n'est plus judicieuse : elle dépend non seulement de l'estimateur $\overline{X}$ et de $m$, mais également de la variance $\sigma^2$ inconnue.

Dans un tel cas, on commence par estimer $\sigma^2$. L'[[Estimateur du maximum de vraisemblance|estimateur du maximum de vraisemblance]] fournit

$$\widehat{\sigma}^2 = \frac{1}{n} \sum_{i=1}^{n} (X_i - m)^2,$$

qui possède les qualités requises, mais nécessite la connaissance de $m$, inconnu. On se contente donc des estimateurs $S^2$ ou $S'^2$ :

$$S^2 = \frac{1}{n} \sum_{i=1}^{n} (X_i - \overline{X})^2$$

$$S'^2 = \frac{1}{n-1} \sum_{i=1}^{n} (X_i - \overline{X})^2,$$

où $S^2$ est la [[Variance empirique|variance empirique]] et $S'^2$ la variance empirique corrigée, [[Biais d'un estimateur|estimateur sans biais]] de $\sigma^2$.

D'après le [[Théorème de Student pour la moyenne empirique|théorème de Student pour la moyenne empirique]], la variable

$$T_{n-1} = \frac{\overline{X} - m}{\sqrt{\frac{S'^2}{n}}}$$

suit une [[Loi de Student|loi de Student]] $\mathcal{T}_{n-1}$ à $n-1$ degrés de liberté. La densité d'une loi de Student est symétrique et sa fonction de répartition est tabulée : on considère donc un intervalle de confiance symétrique et, à l'aide de la table d'une loi de Student à $n-1$ degrés de liberté, on détermine $t_{n-1, \frac{\alpha}{2}}$ tel que

$$\mathbb{P} \left[ -t_{n-1, \frac{\alpha}{2}} \leq T_{n-1} \leq t_{n-1, \frac{\alpha}{2}} \right] = 1 - \alpha.$$

Ainsi, on obtient

$$\mathbb{P} \left[ \overline{X} - t_{n-1, \frac{\alpha}{2}} \frac{S'}{\sqrt{n}} \leq m \leq \overline{X} + t_{n-1, \frac{\alpha}{2}} \frac{S'}{\sqrt{n}} \right] = 1 - \alpha,$$

et, pour l'[[Échantillon et échantillonnage|échantillon]] observé $(x_1, \dots, x_n)$, l'intervalle de confiance de $m$ au niveau de confiance $1 - \alpha$ est

$$\left[ \overline{x} - t_{n-1, \frac{\alpha}{2}} \frac{s'}{\sqrt{n}}, \overline{x} + t_{n-1, \frac{\alpha}{2}} \frac{s'}{\sqrt{n}} \right],$$

soit encore

$$\left[ \overline{x} - t_{n-1, \frac{\alpha}{2}} \frac{s}{\sqrt{n-1}}, \overline{x} + t_{n-1, \frac{\alpha}{2}} \frac{s}{\sqrt{n-1}} \right].$$

# Remarque

Il est plus simple de retenir le résultat sous la forme

$$\frac{\overline{X} - m}{\sqrt{\frac{S'^2}{n}}} \sim \mathcal{T}_{n-1},$$

car il suffit de se rappeler que l'on obtient $T_{n-1}$ en remplaçant $\sigma^2$ par son estimateur sans biais $S'^2$ dans la fonction $g$ ; ainsi faisant, la loi n'est plus $\mathcal{N}(0, 1)$ mais $\mathcal{T}_{n-1}$.

On peut penser que, si $n$ est grand, on devrait pouvoir remplacer $\sigma^2$ par $s'^2$ dans l'application numérique de l'intervalle sans introduire une grosse erreur. C'est bien le cas : si $n$ est grand (généralement $n > 30$), la loi de Student est correctement approchée par la loi $\mathcal{N}(0, 1)$.

Pour l'application numérique, au lieu de calculer $s'$ par la définition

$$s' = \sqrt{\frac{1}{n-1} \sum_{i=1}^{n} (x_i - \overline{x})^2},$$

on calcule en général plus vite $s^2$ à l'aide de la formule

$$s^2 = \overline{x^2} - \overline{x}^2,$$

où $\overline{x^2} = \frac{1}{n} \sum_{i=1}^{n} x_i^2$ est la moyenne des carrés des observations, puis on calcule $\frac{s'}{\sqrt{n}}$ en utilisant

$$\frac{s'}{\sqrt{n}} = \frac{s}{\sqrt{n-1}}.$$

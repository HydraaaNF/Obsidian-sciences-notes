# Théorème

Soient $(X_1, \dots, X_{n_1})$ et $(Y_1, \dots, Y_{n_2})$ deux échantillons gaussiens indépendants, de [[Loi de la variance empirique corrigée|variances empiriques corrigées]]

$$(S_1')^2 = \frac{1}{n_1 - 1} \sum_{i=1}^{n_1} (X_i - \overline{X})^2$$

$$(S_2')^2 = \frac{1}{n_2 - 1} \sum_{i=1}^{n_2} (Y_i - \overline{Y})^2.$$

Le test de Fisher d'égalité de variances confronte l'[[Hypothèse nulle et hypothèse alternative|hypothèse nulle]] $H_0 : \sigma_1 = \sigma_2$ à l'hypothèse alternative $H_1 : \sigma_1 \neq \sigma_2$, où $\sigma_1$ et $\sigma_2$ sont les écarts-types des lois mères $\mathcal{N}(m_1, \sigma_1^2)$ et $\mathcal{N}(m_2, \sigma_2^2)$. Dans le cas de deux échantillons gaussiens, on a sous l'hypothèse $H_0$ d'égalité des variances

$$\frac{(S_1')^2}{(S_2')^2} \quad \text{suit une loi de Fisher } \mathcal{F}(n_1 - 1, n_2 - 1),$$

où $\mathcal{F}(n_1 - 1, n_2 - 1)$ désigne la [[Loi de Fisher|loi de Fisher]] à $n_1 - 1$ et $n_2 - 1$ degrés de liberté.

### Démonstration

L'échantillon $(X_1, \dots, X_{n_1})$, de loi mère $\mathcal{N}(m_1, \sigma_1^2)$, est associé à la variance empirique $S_1^2 = \frac{1}{n_1} \sum_{i=1}^{n_1} (X_i - \overline{X})^2$ et l'échantillon $(Y_1, \dots, Y_{n_2})$, de loi mère $\mathcal{N}(m_2, \sigma_2^2)$, à la variance empirique $S_2^2 = \frac{1}{n_2} \sum_{i=1}^{n_2} (Y_i - \overline{Y})^2$. Ces variances empiriques sont liées aux variances empiriques corrigées par $n_1 S_1^2 = (n_1 - 1)(S_1')^2$ et $n_2 S_2^2 = (n_2 - 1)(S_2')^2$.

On a alors

$$\frac{n_1 S_1^2}{\sigma_1^2} = \frac{(n_1 - 1) (S_1')^2}{\sigma_1^2} = \sum_{i=1}^{n_1} \left( \frac{X_i - \overline{X}}{\sigma_1} \right)^2 \text{ suit une loi } \chi_{n_1-1}^2,$$

et de même

$$\frac{n_2 S_2^2}{\sigma_2^2} = \frac{(n_2 - 1) (S_2')^2}{\sigma_2^2} = \sum_{i=1}^{n_2} \left( \frac{Y_i - \overline{Y}}{\sigma_2} \right)^2 \text{ suit une loi } \chi_{n_2-1}^2.$$

Les échantillons $(X_1, \dots, X_{n_1})$ et $(Y_1, \dots, Y_{n_2})$ étant indépendants, ces deux variables le sont également, et l'on a donc

$$\frac{\frac{n_1 S_1^2}{\sigma_1^2} \ast \frac{1}{n_1 - 1}}{\frac{n_2 S_2^2}{\sigma_2^2} \ast \frac{1}{n_2 - 1}} = \frac{\frac{(S_1')^2}{\sigma_1^2}}{\frac{(S_2')^2}{\sigma_2^2}} \quad \text{suit une loi de Fisher } \mathcal{F}(n_1 - 1, n_2 - 1).$$

# Algorithme

Pour un [[Risque de première espèce|risque de première espèce]] $\alpha$, on cherche $a$ et $b$ tels que

$$\mathbb{P}_{H_0}\left[\frac{(S_1')^2}{(S_2')^2} > b\right] = \frac{\alpha}{2}$$

$$\mathbb{P}_{H_0}\left[\frac{(S_1')^2}{(S_2')^2} < a\right] = \frac{\alpha}{2}$$

d'où

$$\mathbb{P}_{H_0}\left[a \leq \frac{(S_1')^2}{(S_2')^2} \leq b\right] = 1 - \alpha.$$

Compte-tenu de la forme de la table de loi de Fisher, on est généralement obligé de considérer la loi de $\frac{(S_2')^2}{(S_1')^2}$ pour obtenir la valeur du seuil $a$. En effet, sous $H_0$,

$$\frac{(S_2')^2}{(S_1')^2} \quad \text{suit une loi de Fisher } \mathcal{F}(n_2 - 1, n_1 - 1).$$

- si $\frac{(s_1')^2}{(s_2')^2} \in [a, b]$, on accepte $H_0$ et on procède au [[Test de Student d'égalité de deux moyennes|test d'égalité des moyennes]] ;
- sinon, on conclut que $\sigma_1 \neq \sigma_2$ avec la probabilité $\alpha$ de se tromper. On conclut également que les deux échantillons ne sont pas homogènes et on n'effectue pas le test sur les moyennes.

# Remarque

Le test de Fisher d'égalité de variances est la première étape du [[Test d'homogénéité de deux échantillons gaussiens|test d'homogénéité de deux échantillons gaussiens]] : l'égalité des variances doit être acceptée avant de tester l'égalité des moyennes.

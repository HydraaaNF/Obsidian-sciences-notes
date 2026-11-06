# Modèle

Le test de Student d'égalité de deux moyennes s'applique à deux [[Échantillon et échantillonnage|échantillons]] indépendants $(X_1, \dots, X_{n_1})$ et $(Y_1, \dots, Y_{n_2})$ issus de [[Loi gaussienne|lois mères gaussiennes]] de même variance. Il constitue la seconde étape du [[Test d'homogénéité de deux échantillons gaussiens|test d'homogénéité de deux échantillons gaussiens]] : l'égalité des variances est d'abord testée à l'aide du [[Test de Fisher d'égalité de variances|test de Fisher]] et, si elle est acceptée, on teste l'[[Hypothèse nulle et hypothèse alternative|hypothèse nulle]] $H_0$ contre l'hypothèse alternative $H_1$, soit

$$H_0 : m_1 = m_2 \quad \text{contre} \quad H_1 : m_1 \neq m_2.$$

Selon le contexte, $H_1$ peut également être de la forme $m_1 > m_2$ ou $m_1 < m_2$.

Les échantillons sont respectivement associés aux lois mères $\mathcal{N}(m_1, \sigma^2)$ et $\mathcal{N}(m_2, \sigma^2)$, avec $\sigma_1 = \sigma_2 = \sigma$. On note $\overline{X} = \frac{1}{n_1} \sum_{i=1}^{n_1} X_i$ et $\overline{Y} = \frac{1}{n_2} \sum_{i=1}^{n_2} Y_i$ les [[Moyenne empirique|moyennes empiriques]] des deux échantillons. On a donc

$$\overline{X} \sim \mathcal{N}\left(m_1, \frac{\sigma^2}{n_1}\right)$$

$$\overline{Y} \sim \mathcal{N}\left(m_2, \frac{\sigma^2}{n_2}\right).$$

# Théorème

Dans le cas de deux échantillons gaussiens de variance identique, on a sous l'hypothèse $H_0$ d'égalité des espérances

$$\frac{\overline{X} - \overline{Y}}{S^* \sqrt{\frac{1}{n_1} + \frac{1}{n_2}}} \sim \mathcal{T}_{n_1+n_2-2},$$

où $(S^*)^2 = \frac{(n_1-1)(S'_1)^2 + (n_2-1)(S'_2)^2}{n_1+n_2-2}$ est l'estimateur de la variance commune $\sigma^2$ construit à partir des deux échantillons.

La variable aléatoire décrite ci-dessus joue le rôle de [[Statistique de test|statistique de test]]. Sa [[Zone critique et seuil d'un test|zone critique]] se détermine à l'aide de la table de la [[Loi de Student|loi de Student]] à $n_1 + n_2 - 2$ degrés de liberté, selon la forme de $H_1$ et le [[Risque de première espèce|risque de première espèce]] $\alpha$ ; la lecture à double entrée de cette table est décrite dans [[Lecture d'une table de probabilité]].

### Démonstration

Les deux échantillons étant indépendants, on en déduit que

$$\overline{X} - \overline{Y} \sim \mathcal{N}\left(m_1 - m_2, \sigma^2 \left(\frac{1}{n_1} + \frac{1}{n_2}\right)\right),$$

d'où

$$U = \frac{\overline{X} - \overline{Y} - (m_1 - m_2)}{\sigma \sqrt{\frac{1}{n_1} + \frac{1}{n_2}}} \sim \mathcal{N}(0,1).$$

Étant donné que $\sigma$ est inconnu, on se sert des deux échantillons pour estimer $\sigma^2$, comme dans le [[Théorème de Student pour la moyenne empirique|théorème de Student pour la moyenne empirique]]. On pose

$$\begin{aligned} (S^*)^2 &= \frac{\sum_{i=1}^{n_1}(X_i-\overline{X})^2+\sum_{i=1}^{n_2}(Y_i-\overline{Y})^2}{n_1+n_2-2} \\ &= \frac{n_1S_1^2+n_2S_2^2}{n_1+n_2-2} \\ &= \frac{(n_1-1)(S'_1)^2+(n_2-1)(S'_2)^2}{n_1+n_2-2}, \end{aligned}$$

où $S_1^2$ et $S_2^2$ sont les [[Variance empirique|variances empiriques]] des deux échantillons et $(S'_1)^2$ et $(S'_2)^2$ les [[Loi de la variance empirique corrigée|variances empiriques corrigées]] :

$$S_1^2 = \frac{1}{n_1} \sum_{i=1}^{n_1} (X_i - \overline{X})^2$$

$$(S'_1)^2 = \frac{1}{n_1-1} \sum_{i=1}^{n_1} (X_i - \overline{X})^2,$$

$$S_2^2 = \frac{1}{n_2} \sum_{i=1}^{n_2} (Y_i - \overline{Y})^2$$

$$(S'_2)^2 = \frac{1}{n_2-1} \sum_{i=1}^{n_2} (Y_i - \overline{Y})^2.$$

Comme $(S'_1)^2$ et $(S'_2)^2$ sont des [[Estimateur|estimateurs]] de $\sigma^2$ [[Estimateur fortement convergent|fortement convergents]] et [[Biais d'un estimateur|sans biais]], on vérifie que $(S^*)^2$ l'est également.

Par ailleurs, étant donné que $(S'_1)^2$ et $(S'_2)^2$ sont des variables aléatoires indépendantes et que les lois mères sont gaussiennes, on a

$$\frac{(n_1-1)(S'_1)^2}{\sigma^2} \sim \chi_{n_1-1}^2$$

$$\frac{(n_2-1)(S'_2)^2}{\sigma^2} \sim \chi_{n_2-1}^2,$$

où $\chi_n^2$ désigne la [[Loi du chi-deux|loi du chi-deux]] à $n$ degrés de liberté. On en déduit que

$$V = (n_1 + n_2 - 2) \frac{(S^*)^2}{\sigma^2} = \frac{(n_1 - 1)(S'_1)^2}{\sigma^2} + \frac{(n_2 - 1)(S'_2)^2}{\sigma^2} \sim \chi_{n_1+n_2-2}^2.$$

En combinant ces résultats, on obtient

$$\frac{U}{\sqrt{\frac{V}{n_1+n_2-2}}} \sim \mathcal{T}_{n_1+n_2-2},$$

soit sous $H_0$

$$\frac{\overline{X} - \overline{Y}}{\sigma \sqrt{\frac{1}{n_1} + \frac{1}{n_2}}} \frac{\sigma}{S^*} \sim \mathcal{T}_{n_1+n_2-2}.$$

En simplifiant, on obtient la statistique du théorème.

# Propriétés

La quantité $(S^*)^2$ s'écrit aussi, avec les [[Variance empirique|variances empiriques]] $S_1^2$ et $S_2^2$,

$$S_p^2 = \frac{n_1 S_1^2 + n_2 S_2^2}{n_1 + n_2 - 2},$$

et la statistique prend la forme équivalente

$$T_{n_1+n_2-2} = \frac{(\overline{X} - \overline{Y}) - (m_1 - m_2)}{S_p\sqrt{\frac{1}{n_1} + \frac{1}{n_2}}}.$$

Sous $H_0$, le terme $m_1 - m_2$ est nul : la statistique se réduit au rapport de la différence des moyennes empiriques à l'écart type estimé de cette différence. Le dénominateur $S_p\sqrt{\frac{1}{n_1} + \frac{1}{n_2}}$ est l'écart type estimé de cet écart, obtenu en combinant les deux variances empiriques.

La variance commune $S_p^2$ est une moyenne pondérée des deux variances empiriques, de poids $n_i$ et de diviseur $n_1 + n_2 - 2$. Elle suppose les deux variances égales : les deux échantillons apportent alors deux estimations de la même dispersion, que l'on met en commun pour gagner en précision.

Lorsque les variances sont inégales, la mise en commun $S_p^2$ n'est pas légitime et la statistique ne suit plus une loi de Student à $n_1 + n_2 - 2$ degrés de liberté : il faut alors corriger le nombre de degrés de liberté, qui devient une quantité fractionnaire dépendant des variances estimées.

# Remarque

Si les échantillons sont indépendants sans être gaussiens mais de taille suffisamment importante (quelques dizaines), on ne peut plus effectuer le test de Fisher sur l'égalité des variances. On peut cependant tester l'égalité des moyennes en appliquant la formule de Student, que $\sigma_1$ soit différent ou non de $\sigma_2$ : on dit que le test de Student est **robuste au changement de loi**.

Ce test généralise au cas de deux échantillons le [[Test de comparaison d'une moyenne à une valeur donnée|test de comparaison d'une moyenne à une valeur donnée]].

Des échantillons appariés, où les mêmes individus sont mesurés deux fois, ne relèvent pas de ce test mais d'un test sur les différences individuelles : voir [[Comparaison d'échantillons appariés]].

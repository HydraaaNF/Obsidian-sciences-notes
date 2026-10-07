# Modèle

Un test de comparaison de deux proportions confronte une [[Hypothèse nulle et hypothèse alternative|hypothèse nulle]] $H_0$ à une hypothèse alternative $H_1$ à partir de deux [[Échantillon et échantillonnage|échantillons]] indépendants $(X_1, \ldots, X_{n_1})$ et $(Y_1, \ldots, Y_{n_2})$, issus d'une loi mère de [[Loi de Bernoulli|Bernoulli]] de paramètres $p_1$ et $p_2$ respectivement. On souhaite tester l'hypothèse

$$H_0 : p = p_1 = p_2$$

contre l'hypothèse composite $H_1 : p_1 \neq p_2$ (ou $p_1 > p_2$, $p_1 < p_2$). Un tel test peut correspondre à la comparaison de deux sondages lors d'une campagne électorale (évolution d'un score estimé d'un candidat par exemple).

De manière similaire à l'[[Intervalle de confiance d'une proportion|estimation d'une proportion par intervalle]], si les échantillons sont de grande taille, on peut approcher la [[Loi de Student|loi de Student]] par la [[Loi gaussienne|loi normale centrée réduite]]. On obtient alors comme [[Statistique de test|statistique de test]], sous $H_0$,

$$\frac{\overline{X} - \overline{Y}}{\sqrt{F(1-F)}\sqrt{\frac{1}{n_1} + \frac{1}{n_2}}} \sim \mathcal{N}(0,1)$$

où $\overline{X} = \frac{1}{n_1} \sum_{i=1}^{n_1} X_i$ et $\overline{Y} = \frac{1}{n_2} \sum_{j=1}^{n_2} Y_j$ sont les [[Moyenne empirique|moyennes empiriques]] des deux échantillons, et où $F$ est l'[[Estimateur|estimateur]] de $p$ défini par

$$F = \frac{n_1 \overline{X} + n_2 \overline{Y}}{n_1 + n_2}.$$

Selon la forme de l'hypothèse $H_1$ et du [[Risque de première espèce|risque de première espèce]] $\alpha$, on détermine la [[Zone critique et seuil d'un test|zone critique]] à l'aide de la table de la loi $\mathcal{N}(0, 1)$.

# Remarque

L'approximation par la loi normale centrée réduite repose sur le [[Théorème de la limite centrale|théorème de la limite centrale]] et n'est valable que pour des échantillons de grande taille.

Pour deux échantillons gaussiens de variance identique, l'égalité de deux moyennes se teste avec le [[Test de Student d'égalité de deux moyennes]].

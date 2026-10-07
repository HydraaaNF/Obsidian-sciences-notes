# Définition

**Estimation par maximum de vraisemblance.** Le paramètre $\theta$ du modèle est estimé par

$$\hat{\theta} = \arg \max_{\theta} p(x; \theta)$$

L'estimateur ainsi défini est l'[[Estimateur du maximum de vraisemblance]].

**Classification.** La règle du maximum a posteriori retient la classe

$$\hat{c} = \arg \max_c p(c|x) = \arg \max_c p(x|c)p(c)$$

et la règle du maximum de vraisemblance retient la classe

$$\hat{c} = \arg \max_c p_c(x)$$

**Test d'hypothèses.** Le rapport de vraisemblance

$$\frac{p(x; H_0)}{p(x; H_1)}$$

est comparé à un seuil $\beta$ : s'il est supérieur à $\beta$, l'hypothèse $H_0$ est retenue ; s'il est inférieur, l'hypothèse $H_1$ est retenue.

# Remarque

En classification, le maximum de vraisemblance est un cas particulier du maximum a posteriori lorsque la loi a priori des classes est uniforme, $p(c) \sim \mathcal{U}$. Voir la [[Règle de décision de Bayes]] et le [[Classifieur naïf de Bayes]] pour ces règles de classification.

La forme correcte est « estimation » ; l'écriture « esimtation » est une coquille fréquente.

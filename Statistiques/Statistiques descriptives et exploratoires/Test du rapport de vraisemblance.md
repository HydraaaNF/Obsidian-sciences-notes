#adm-9

# Définition

Le test du rapport de vraisemblance confronte une valeur postulée d'un paramètre à l'ensemble des valeurs possibles, en comparant la vraisemblance des données sous cette valeur à la meilleure vraisemblance atteignable. Il généralise le [[Lemme de Neyman-Pearson]], établi pour des hypothèses simples, au cas d'hypothèses composites.

Soit $\theta \in \mathbb{R}^p$ le paramètre inconnu et $\mathbf{x}$ l'échantillon observé. Le test oppose l'hypothèse simple $H_0$, qui fixe $\theta$ à la valeur unique $\theta_0$, à l'hypothèse composite $H_1$, qui laisse à $\theta$ toute autre valeur :

- $H_0$ : $\theta = \theta_0$ ;
- $H_1$ : $\theta \neq \theta_0$.

La statistique du test est le **rapport de vraisemblance**

$$
\lambda = \frac{L(\mathbf{x}; \theta_0)}{\sup_{\theta} L(\mathbf{x}; \theta)}
$$

où $L$ désigne la [[Fonction de vraisemblance|fonction de vraisemblance]] de l'échantillon.

La [[Zone critique et seuil d'un test|région critique]] est de la forme

$$
\{\mathbf{x} \mid \lambda < K_\alpha\}
$$

où $K_\alpha$ est le seuil fixé en fonction du [[Risque de première espèce|risque de première espèce]] $\alpha$.

# Propriétés

Sous $H_0$, la statistique transformée suit asymptotiquement une [[Loi du chi-deux]] à $p$ degrés de liberté, $p$ étant la dimension du paramètre :

$$
-2 \ln(\lambda) \rightsquigarrow \chi_p^2
$$

# Interprétation

Le numérateur évalue la vraisemblance des données sous la valeur postulée par $H_0$ ; le dénominateur retient la meilleure vraisemblance sur tout l'espace des paramètres. Le rapport est donc compris entre $0$ et $1$.

Un rapport proche de $1$ signifie que $H_0$ explique les données presque aussi bien que la meilleure valeur possible du paramètre, ce qui conduit à la conserver ; un rapport petit signale que les données sont mal expliquées par $\theta_0$, ce qui conduit à rejeter $H_0$ dès que $\lambda < K_\alpha$.

# Remarque

Remplacer $L(\mathbf{x}; \theta_0)$ par $\sup_{\theta} L(\mathbf{x}; \theta)$ revient à utiliser l'[[Estimateur du maximum de vraisemblance|estimation du maximum de vraisemblance]] de $\theta$ : le dénominateur est la vraisemblance évaluée en cet estimateur, et le rapport mesure donc l'écart entre la vraisemblance sous $H_0$ et la vraisemblance maximale.

La démarche est fréquentiste : elle compare des vraisemblances sous des hypothèses et fixe le seuil par le [[Risque de première espèce|risque de première espèce]], sans probabilité a priori sur les hypothèses. La [[Règle de décision de Bayes|règle de décision de Bayes]] suit la démarche inverse, en pondérant les vraisemblances par des probabilités a priori pour minimiser un risque moyen.

Le test constitue l'une des grandes [[Familles de tests statistiques|familles de tests statistiques]], aux côtés des tests d'ajustement et des tests de comparaison de deux populations.

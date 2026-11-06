# Théorème

Soit $X$ une variable aléatoire de densité $f(x;\theta)$, et soit $L(\mathbf{x};\theta)$ la densité de l'[[Échantillon et échantillonnage|échantillon]] $\mathbf{x}$ (la [[Fonction de vraisemblance|vraisemblance]] de cet échantillon). On considère le test de deux [[Hypothèse nulle et hypothèse alternative|hypothèses]] simples

$$\begin{aligned} H_0 &: \theta = \theta_0 \\ H_1 &: \theta = \theta_1 \end{aligned}$$

Parmi tous les tests de [[Risque de première espèce|risque de première espèce]] $\alpha$ fixé, celui qui maximise la [[Puissance d'un test|puissance]] rejette $H_0$ pour les échantillons dont le rapport des vraisemblances dépasse un certain seuil :

$$W = \left\{ \mathbf{x} \mid \frac{L(\mathbf{x};\theta_1)}{L(\mathbf{x};\theta_0)} > k_\alpha \right\}$$

où $W$ est la [[Zone critique et seuil d'un test|région critique]] du test et $k_\alpha$ le seuil déterminé par le niveau $\alpha$.

La puissance de ce test s'écrit

$$\mathbb{P}[W \mid H_1] = 1 - \beta = \int_W L(\mathbf{x};\theta_1) \, dx$$

où $\beta$ désigne le [[Risque de seconde espèce|risque de seconde espèce]].

# Interprétation

Le rapport $L(\mathbf{x};\theta_1) / L(\mathbf{x};\theta_0)$ mesure combien l'échantillon observé est plus vraisemblable sous $H_1$ que sous $H_0$. La région critique optimale rassemble donc les observations qui soutiennent le plus fortement $H_1$ : on rejette $H_0$ dès que ce rapport franchit le seuil $k_\alpha$.

Le seuil $k_\alpha$ arbitre le compromis entre les deux risques : plus $k_\alpha$ est grand, plus le test est exigeant avant de rejeter $H_0$, donc plus le risque de première espèce est faible et plus le [[Risque de seconde espèce|risque de seconde espèce]] est élevé.

# Remarque

Le lemme ne s'applique qu'à deux hypothèses simples, c'est-à-dire fixant chacune la valeur du paramètre : le risque $\beta$, et donc la puissance, ne dépend alors d'aucune valeur inconnue. Lorsque les hypothèses sont composites, le risque de seconde espèce dépend de $\theta$ et la démarche se généralise en remplaçant $L(\mathbf{x};\theta_1)$ par la plus grande vraisemblance atteignable sur l'ensemble des valeurs de $\theta$ : c'est le [[Test du rapport de vraisemblance|test du rapport de vraisemblance]].

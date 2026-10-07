# Définition

Dans un test d'hypothèses opposant une [[Hypothèse nulle et hypothèse alternative|hypothèse nulle]] $H_0$ à une hypothèse alternative $H_1$, la décision repose sur l'observation de la [[Moyenne empirique|moyenne empirique]] $\overline{X}$ : on conserve $H_0$ lorsque cette observation appartient à un intervalle $\mathcal{D}$, et on la rejette sinon, l'ensemble $\mathcal{D}^c$ étant la [[Zone critique et seuil d'un test|région critique]] du test. La probabilité d'accepter $H_0$ à tort, c'est-à-dire lorsque $H_1$ est vraie, est notée

$$\beta = \mathbb{P}_{H_1}[\overline{X} \in \mathcal{D}]$$

et appelée **risque de seconde espèce**.

# Interprétation

Il ne faut pas confondre le risque de seconde espèce avec le [[Risque de première espèce]] : $\alpha$ est la probabilité de rejeter $H_0$ à tort, tandis que $\beta$ est la probabilité de conserver $H_0$ à tort. Dans l'exemple des faiseurs de pluie, $\alpha$ représente le risque d'investir dans un procédé inefficace et $\beta$ le risque de passer à côté de meilleures récoltes en n'investissant pas dans un procédé efficace.

Généralement, lorsque l'on effectue un test statistique, **on choisit $H_0$ de telle manière que les conséquences de l'erreur de seconde espèce soient moins graves que celles de l'erreur de première espèce** : autrement dit, $H_0$ correspond à une idée de « principe de précaution ». Pour illustrer cette idée, en cas de risque de pandémie de grippe A, on poserait l'hypothèse $H_0$ correspondant à « une gravité importante de la pandémie » contre $H_1$ où « la pandémie ne serait pas si grave » : le risque de première espèce correspondrait alors à l'insuffisance du nombre de doses de vaccins face à une grave pandémie, tandis que le risque de seconde espèce correspondrait à un investissement financier surdimensionné par rapport à la gravité relative de la pandémie.

# Exemple

Dans l'exemple des faiseurs de pluie, l'hypothèse $H_1$ est une hypothèse simple ($m = 650$) et la zone critique du test est $]654{,}83 ; +\infty[$ : le calcul du risque de seconde espèce y est donc possible. On commet l'erreur de seconde espèce lorsque $H_1$ est vraie et que $\overline{X}$ n'est pas dans la zone critique, ce qui amène à conserver $H_0$ à tort. Ainsi,

$$\beta = \mathbb{P}_{H_1}[\overline{X} \leq 654{,}83],$$

où sous $H_1$,

$$\overline{X} \sim \mathcal{N}\left(650, \frac{100^2}{9}\right),$$

c'est-à-dire

$$\frac{\overline{X} - 650}{100} \times 3 \sim \mathcal{N}(0, 1).$$

On en déduit la valeur de $\beta$ à l'aide de la [[Quantile de la loi normale centrée réduite|table de la loi normale centrée réduite]] :

$$\begin{aligned}
\beta &= \mathbb{P}_{H_1}\left[\frac{\overline{X} - 650}{100} \times 3 \leq \frac{654{,}83 - 650}{100} \times 3\right] \\
&= \mathbb{P}_{H_1}\left[\frac{\overline{X} - 650}{100} \times 3 \leq 0{,}144\right] \\
&= 0{,}55.
\end{aligned}$$

Par conséquent, en ne prenant pas le risque d'acheter le produit, on a 55 % de chances de passer à côté d'un procédé qui augmente de 50 mm le niveau de pluie par an et permet de meilleures récoltes.

# Remarque

Le calcul du risque de seconde espèce est possible lorsque l'hypothèse $H_1$ est une hypothèse simple, c'est-à-dire lorsqu'elle fixe la valeur du paramètre testé : c'est le cas de l'exemple des faiseurs de pluie, avec $H_1 : m = 650$. Le risque de seconde espèce forme avec le [[Risque de première espèce]] le couple des risques d'erreur d'un test, et il intervient dans la [[Puissance d'un test|puissance du test]].

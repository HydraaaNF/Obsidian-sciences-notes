#adm-0bis #adm-9

# Définition

La **zone critique** (ou **région critique**) d'un test est la partie des valeurs de la [[Statistique de test|statistique de test]] pour laquelle on rejette l'[[Hypothèse nulle et hypothèse alternative|hypothèse nulle]] $H_0$ au profit de l'hypothèse alternative $H_1$. Compte tenu de la forme de $H_1$, elle est de la forme $]a, +\infty[$ ou de la forme $]-\infty, a[$ selon le sens du test.

Le **seuil** du test est la valeur frontière $a$ de la zone critique. Il est déterminé de sorte que la probabilité de rejeter $H_0$ à tort (c'est-à-dire lorsque $H_0$ est vraie) soit égale au [[Risque de première espèce|risque de première espèce]] $\alpha$ fixé. Pour une zone critique de la forme $]a, +\infty[$, on détermine ainsi $a$ tel que

$$\mathbb{P}_{H_0}[\overline{X} > a] = \alpha.$$

# Propriétés

La forme de la zone critique et la position de son seuil relèvent de deux hypothèses différentes.

La **forme** de la zone critique est dictée par l'[[Hypothèse nulle et hypothèse alternative|hypothèse alternative]] $H_1$ : c'est elle qui situe les valeurs conduisant à rejeter $H_0$ d'un côté ou de l'autre de celles postulées sous $H_0$, et qui décide donc si la zone critique est unilatérale ou bilatérale.

Le **seuil** $a$ ne dépend que de $H_0$ et du [[Risque de première espèce|risque de première espèce]] $\alpha$ : il est placé de façon que, sous $H_0$, la probabilité de tomber dans la zone critique vaille $\alpha$. Une connaissance plus précise de $H_1$ n'intervient pas dans ce placement ; elle sert à calculer le [[Risque de seconde espèce|risque de seconde espèce]] $\beta$, donc la [[Puissance d'un test|puissance]] du test.

# Exemple

Dans l'exemple des faiseurs de pluie, le test compare $H_0 : m = 600$ à $H_1 : m = 650$ pour la moyenne $\overline{X}$ d'un échantillon, avec un risque de première espèce $\alpha = 0{,}05$. Compte tenu de la forme de l'hypothèse $H_1$, la zone critique du test est de la forme $]a, +\infty[$ : pour rejeter $H_0$ et donc accepter $H_1$ (où $m = 650$), il faut que l'observation de $\overline{X}$ soit « significativement » plus grande que la valeur 600, c'est-à-dire au-delà d'un certain seuil $a$. On détermine $a$ tel que

$$\mathbb{P}_{H_0}[\overline{X} > a] = 0{,}05,$$

$$\text{c'est-à-dire } \mathbb{P}_{H_0}\left[\frac{\overline{X} - 600}{100} \times 3 > \frac{a - 600}{100} \times 3\right] = 0{,}05.$$

Comme sous $H_0$,

$$\frac{\overline{X} - 600}{100} \times 3 \sim \mathcal{N}(0, 1),$$

on en déduit, d'après la [[Quantile de la loi normale centrée réduite|table de la loi normale centrée réduite]], que

$$\frac{a - 600}{100} \times 3 = 1{,}645,$$

d'où

$$a = 654{,}83.$$

On calcule ensuite $\bar{x}$ à partir des observations : si $\bar{x}$ est « trop grand » par rapport à 600, c'est-à-dire si $\bar{x} > a$, on rejette alors $H_0$. L'intervalle $]654{,}83 ; +\infty[$ est la région critique du test. Ici, $\bar{x} = 610{,}2$ n'est pas dans la région critique : $H_0$ est acceptée au risque de première espèce $\alpha = 0{,}05$ et les agriculteurs n'achètent pas le procédé.

Le quantile utilisé vaut $1{,}645$ ; le prendre égal à $1{,}64$ conduit au seuil arrondi $655$ mm, qui ne change pas la décision.

Connaître $H_1$ permet ensuite d'évaluer le risque de seconde espèce. Si la méthode était réellement efficace, $\overline{X}$ suivrait une loi normale centrée sur $650$ mm, de même écart type $100/\sqrt{9}$ : une erreur serait commise chaque fois que $\overline{X}$ reste sous le seuil, soit

$$\beta = \mathbb{P}\left[U < \frac{654{,}83 - 650}{100/\sqrt{9}}\right] = 0{,}56$$

où $U$ suit la loi $\mathcal{N}(0, 1)$. Le test ne détecterait donc l'effet réel que dans $44\,\%$ des cas.

# Remarque

La zone critique dépend du sens du test, c'est-à-dire du choix des hypothèses : si les agriculteurs avaient finalement souhaité acheter le procédé, c'est-à-dire rejeter $H_0$, il aurait alors fallu que la zone critique contienne $\bar{x}$ et le risque de première espèce associé aurait été au moins égal à

$$\begin{aligned}
\mathbb{P}_{H_0}[\overline{X} \geq 610] &= \mathbb{P}_{H_0}\left[\frac{\overline{X} - 600}{100} \times 3 \geq \frac{610 - 600}{100} \times 3\right] \\
&= \mathbb{P}_{H_0}\left[\frac{\overline{X} - 600}{100} \times 3 \geq 0{,}3\right] \\
&= 0{,}38.
\end{aligned}$$

Attention toutefois à cette interprétation : si les agriculteurs avaient souhaité en priorité minimiser le risque de se tromper en n'achetant pas le produit, alors les hypothèses sont à modifier : il faut alors tester $H_0$ ($m = 650$) contre $H_1$ ($m = 600$) et imposer un faible risque de première espèce tel que $\alpha = 0{,}05$. La zone critique est alors de la forme $]-\infty, a[$ où $a$ vérifie

$$\begin{aligned}
\mathbb{P}_{H_0}[\overline{X} < a] &= 0{,}05 \\
\text{soit } \mathbb{P}_{H_0}\left[\frac{\overline{X} - 650}{100} \times 3 < \frac{a - 650}{100} \times 3\right] &= 0{,}05.
\end{aligned}$$

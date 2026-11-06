# Définition

Essayer successivement $m$ tests $T_1, \dots, T_m$, chacun de [[Risque de première espèce|niveau]] $\alpha$, puis rejeter $H_0$ dès que l'un d'eux rejette $H_0$, est en soi une procédure de décision : le **méta-test**. Sa règle de rejet s'écrit

$$
\text{rejeter } H_0 \iff \exists i \in \{1, \dots, m\},\ T_i \text{ rejette } H_0
$$

Le méta-test est exactement ce que produit la démarche du [[P-hacking|p-hacking]] : multiplier les tests revient à décider du rejet de $H_0$ avec une probabilité d'erreur qui n'est plus $\alpha$.

# Propriétés

Le niveau du méta-test, c'est-à-dire la probabilité de rejeter $H_0$ alors que $H_0$ est vraie, vaut

$$
\alpha_{\text{meta}} = \mathbb{P}_{H_0}[\exists i,\ T_i \text{ rejette } H_0]
$$

Il est majoré par

$$
\alpha_{\text{meta}} \leqslant \min(1, m\alpha)
$$

Si les $m$ tests sont indépendants, la probabilité qu'aucun ne rejette $H_0$ est $(1 - \alpha)^m$, d'où l'égalité

$$
\alpha_{\text{meta}} = 1 - (1 - \alpha)^m
$$

Cette valeur dépasse $\alpha$ dès que $m \geqslant 2$ et $0 < \alpha < 1$ : le risque de rejet à tort croît avec le nombre de tests, et la borne $m\alpha$ atteint $1$ dès que $m\alpha \geqslant 1$.

# Exemple

Pour $\alpha = 0{,}05$, le niveau effectif du méta-test sous indépendance vaut :

| $m$ | 1 | 2 | 5 | 10 | 20 |
| :--- | :---: | :---: | :---: | :---: | :---: |
| $1 - (1 - 0{,}05)^m$ | 5 % | 10 % | 23 % | 40 % | 64 % |

Avec vingt tests indépendants de niveau $5$ %, la probabilité de rejeter $H_0$ à tort atteint presque deux sur trois.

# Remarque

Le paramètre $\alpha$ qui intervient dans ces énoncés est le niveau du test, c'est-à-dire son [[Risque de première espèce|risque de première espèce]], et non sa [[Puissance d'un test|puissance]] : certains énoncés décrivent des tests « de puissance $\alpha$ », alors que $\alpha$ y désigne la probabilité de rejeter $H_0$ à tort. La puissance est la probabilité de rejeter $H_0$ lorsque $H_1$ est vraie, quantité distincte du niveau.

Le gonflement de $\alpha_{\text{meta}}$ avec $m$ motive les procédures de contrôle du risque global, comme la [[Correction de Bonferroni]] et la [[Procédure de Benjamini-Hochberg]].

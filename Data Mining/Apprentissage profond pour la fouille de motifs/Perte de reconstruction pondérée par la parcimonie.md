#dmv-pattern_mining_vs_deep_learning

# Définition

La perte de reconstruction d'un [[Auto-encodeur de motifs]] ne somme pas les écarts de reconstruction à poids égal : chaque item est pondéré selon sa présence dans les données, de sorte que, dans une base creuse, une erreur sur un item absent coûte moins qu'une erreur sur un item présent.

Pour une transaction $D[i]$ d'une base $D$ à $m$ items, la perte associée aux paramètres $W$ et $b$ est

$$L_\alpha(D[i]; W, b) = \sum_{j \in \{1, \dots, m\}} \left( (1 - D[i,j])\alpha + D[i,j] \right) \left| z_{ij} - D[i,j] \right|$$

où $D[i,j]$ vaut $1$ si l'item $j$ est présent dans la transaction $i$ et $0$ sinon, et $z_{ij}$ est la valeur reconstruite de cet item pour cette transaction.

Le facteur $\left( (1 - D[i,j])\alpha + D[i,j] \right)$ ne dépend que de la présence de l'item, pas de la reconstruction : le prix de l'erreur est fixé avant que celle-ci soit mesurée.

# Propriétés

Le poids d'un item ne prend que deux valeurs :

- un item présent, $D[i,j] = 1$, pèse $1$ ;
- un item absent, $D[i,j] = 0$, pèse $\alpha$.

Le coefficient $\alpha$ est la proportion de 1 dans la base, c'est-à-dire la densité des données, et donc l'indicateur inverse de leur parcimonie :

$$\alpha = \frac{\#1s}{\#1s + \#0s}$$

Les quantités $\#1s$ et $\#0s$ comptent les 1 et les 0 de l'ensemble de la base : $\alpha$ caractérise $D$ et non la transaction courante.

Comme $\alpha$ est un rapport de comptages, il décroît quand les 0 deviennent majoritaires : plus la base est creuse, plus $\alpha$ est petit, et moins une erreur sur un item absent coûte cher face à une erreur sur un item présent. Le rapport des deux poids est $\alpha : 1$ : une erreur sur un item absent coûte $\alpha$ fois une erreur sur un item présent.

Chaque terme de la somme est une erreur absolue pondérée : la perte est donc de la famille de la [[Perte absolue et perte quadratique|perte absolue]], et c'est d'elle que la [[Rétropropagation]] tire les dérivées par rapport à $W$ et à $b$ lors de la [[Boucle d'apprentissage de l'auto-encodeur de motifs|boucle d'apprentissage]].

# Interprétation

Dans une base creuse, les 0 écrasent les 1 en nombre : une perte qui compterait chaque item pour une unité serait dominée par les 0, et les 1 présents, seuls porteurs des motifs, ne pèseraient presque rien dans le total.

La pondération ramène la contribution des 0 à leur fréquence : la masse des erreurs commises sur les 0 vaut au plus $\alpha\,\#0s$, majorant atteint seulement si tous les 0 sont reconstruits à 1, et cette masse maximale vaut

$$\alpha\,\#0s = \frac{\#1s\,\#0s}{\#1s + \#0s} = p_0\,\#1s \le \#1s$$

où $p_0 = \#0s/(\#1s + \#0s)$ est la proportion de 0. Les 0, quelle que soit leur abondance, ne peuvent donc pas peser collectivement plus que $\#1s$, la masse maximale des erreurs sur les 1, et la reconstruction des items présents, ceux dont les cooccurrences forment les motifs, n'est pas noyée par celle des 0.

Ainsi, dans une base où 5 % des entrées valent 1, $\alpha = 0{,}05$ : une erreur sur un 0 coûte vingt fois moins qu'une erreur sur un 1 de même ampleur, et la masse maximale des erreurs sur les 0 vaut $0{,}95$ fois la masse maximale des erreurs sur les 1.

# Remarque

Cette perte est la quantité $L_{W,b}(X)$ calculée à l'étape de calcul de perte de la [[Boucle d'apprentissage de l'auto-encodeur de motifs|boucle d'apprentissage]], pour la transaction courante $X$ lue comme une ligne $D[i]$ de la base ; les lignes sont des transactions au sens d'[[Items, itemsets et base de transactions]].

La perte dépend des paramètres $W$ et $b$ et de la transaction courante : pour un même réseau, deux transactions de contenus différents n'ont pas le même coût de reconstruction, et c'est l'accumulation de ces coûts sur la base qui guide l'apprentissage.

L'auto-encodeur de motifs est un cas particulier de l'[[Auto-encodeur]] : la présence d'un coefficient de parcimonie dans la perte, absent du cadre général, vient de la nature binaire et creuse des données, où l'immense majorité des entrées de la matrice transactions $\times$ items valent 0.

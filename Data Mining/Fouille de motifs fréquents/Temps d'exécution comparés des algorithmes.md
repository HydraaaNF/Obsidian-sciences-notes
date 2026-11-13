#dmv-frequent_itemsets_mining

Les temps d'exécution de plusieurs algorithmes de fouille d'[[Itemset fréquent|itemsets fréquents]] se comparent sur quatre bases de transactions de tailles et de densités différentes. Pour chaque base, l'axe horizontal porte le [[Support d'un itemset|support minimum absolu]] demandé et l'axe vertical le logarithme décimal du temps d'exécution exprimé en secondes :

$$y = \log_{10} t$$

où $t$ est le temps d'exécution en secondes. Une courbe basse correspond donc à un algorithme rapide, et un écart d'une unité sur l'axe vertical correspond à un facteur dix sur le temps mesuré.

# Interprétation

Les courbes se lisent de trois façons.

**Apriori n'est jamais le plus rapide.** Sur les quatre bases, la courbe d'[[Algorithme Apriori|Apriori]] figure parmi les plus hautes, et c'est elle qui domine toutes les autres sur `chess` et sur `census`, ainsi que sur la première moitié de la plage de `webview1`. Les algorithmes qui évitent la génération de candidats, [[Algorithme Eclat|Eclat]], [[Algorithme FP-growth|FP-growth]], relim et sam, restent en dessous sur l'essentiel des plages.

**Le temps décroît quand le support augmente.** Sur les quatre bases, toutes les courbes descendent de gauche à droite : plus la contrainte de fréquence est sévère, plus l'exécution est courte. La pente est forte aux faibles supports et s'aplatit vers les supports élevés : c'est aux faibles supports que les temps d'exécution sont les plus longs.

**Aucun algorithme ne gagne partout.** Eclat, deuxième sur `chess` et `census`, est la courbe la plus haute de `T10I4D100K` sur toute la plage mesurée, Apriori ne s'en rapprochant qu'au plus faible support, alors que FP-growth y figure parmi les plus basses. Le classement dépend donc de la base, et pas seulement du principe de l'algorithme.

# Exemple

| Base | Support minimum absolu | Algorithmes comparés | Plus rapide | Plus lent |
|---|---|---|---|---|
| `chess` | 1000 à 2000 | Apriori, Eclat, FP-growth, relim, sam | FP-growth, relim et sam, confondus | Apriori |
| `T10I4D100K` | environ 3 à 50 | Apriori, Eclat, FP-growth, relim, sam, relim -h | relim -h | Eclat |
| `census` | environ 5 à 100 | Apriori, Eclat, FP-growth, relim, sam | sam | Apriori |
| `webview1` | 33 à 40 | Apriori, Eclat, FP-growth, relim, sam | FP-growth | sam aux supports les plus élevés |

**Sur `chess`.** Apriori occupe le haut du graphique sur toute la plage, Eclat vient juste en dessous, et FP-growth, relim et sam restent confondus au plus bas, en se croisant. La courbe d'Apriori ne comporte de points qu'à partir du support 1200, alors que les quatre autres algorithmes sont mesurés dès 1000, et à l'extrémité droite les trois courbes basses descendent jusqu'à l'ordonnée la plus basse de l'axe.

**Sur `T10I4D100K`.** Au plus faible support, les courbes partent d'un niveau resserré, Eclat déjà au-dessus. Quand le support augmente, le classement se fige : Eclat reste en haut sur toute la plage, sam et Apriori se disputent la deuxième place, sam passant devant Apriori dès les tout premiers supports mesurés, puis viennent FP-growth, relim et enfin relim -h, qui reste la plus basse sur presque toute la plage. Les courbes de relim et de relim -h sont proches, la variante -h restant sous relim.

**Sur `census`.** Apriori domine nettement, Eclat le suit à distance, puis viennent relim, FP-growth et sam, ce dernier restant la courbe la plus basse, très près de FP-growth aux petits supports.

**Sur `webview1`.** La plage de supports est étroite et élevée. Les cinq courbes partent confondues au support 33 et se séparent ensuite : Apriori et sam occupent le haut, sam passant au-dessus d'Apriori aux supports les plus élevés, FP-growth reste la plus basse sur presque toute la plage, Eclat et relim se situant entre les deux.

# Remarque

Outre [[Algorithme Apriori|Apriori]], [[Algorithme Eclat|Eclat]] et [[Algorithme FP-growth|FP-growth]], la comparaison inclut relim et sam, deux programmes de fouille d'[[Itemset fréquent|itemsets fréquents]] à élimination récursive et à division-fusion, qui offrent en option les variantes pour itemsets fermés et maximaux, ainsi que la variante relim -h de relim.

Le support minimum est absolu, c'est-à-dire exprimé en nombre de transactions : la même abscisse ne désigne pas la même proportion sur deux bases de tailles différentes, et les positions horizontales des quatre graphiques ne se comparent pas entre elles.

Comme l'axe vertical est logarithmique, l'écart entre deux courbes mesure un rapport de temps et non une différence de durées : une unité d'écart vaut un facteur dix, deux unités un facteur cent. Les temps eux-mêmes ne sont pas reportés en clair, seule leur allure se lit, et le coût d'Apriori aux faibles supports, qui croît avec le nombre de candidats, est décrit dans [[Complexité de l'algorithme Apriori]].

# Algorithme

L'**algorithme de Viterbi** résout le [[Décodage d'une séquence d'états|décodage d'une séquence d'états]] d'un [[Modèle de Markov caché|modèle de Markov caché]] : il recherche la séquence d'états la plus probable pour une séquence d'observations donnée. Il travaille sur le [[Treillis|treillis]], dont les colonnes correspondent aux observations successives et les lignes aux états du modèle.

**Principe.** Construire itérativement les meilleurs chemins partiels jusqu'à exploration complète du treillis.

Un **chemin partiel** est la suite d'états empruntée depuis la première observation jusqu'à une observation donnée, en suivant les transitions du modèle. Plusieurs chemins partiels aboutissent à une même case du treillis, c'est-à-dire à un même état pour une même observation : l'algorithme n'en conserve qu'un seul, le meilleur, celui dont la probabilité est la plus grande.

La construction se fait colonne par colonne :

- à la première observation, chaque état ouvre un chemin partiel réduit à cet état ;
- à l'observation suivante, chaque chemin partiel conservé est prolongé par les transitions admissibles, la prolongation étant pondérée par la probabilité que l'observation soit émise dans l'état d'arrivée ;
- pour chaque état, seule la meilleure des prolongations est retenue : les chemins partiels de la colonne précédente sont comparés par un maximum ;
- en même temps que ce maximum, la case d'origine qui le fournit est mémorisée comme prédécesseur de la case courante.

Une fois la dernière colonne atteinte, le meilleur chemin partiel qu'elle contient est le meilleur chemin complet, donc la séquence d'états recherchée. Les prédécesseurs mémorisés en chaque case permettent alors de remonter le treillis, de la dernière colonne vers la première, et de restituer un par un les états de cette séquence.

Le critère maximisé est le logarithme de la probabilité jointe de l'observation et de la séquence d'états (voir [[Probabilités d'un modèle de Markov caché]]) :

$$\ln \mathbb{P}[\mathbf{o},\mathbf{s}] = \ln(\pi_{s_1}) + \ln(b_{s_1}(o_1)) + \sum_{t=2}^{T}\left(\ln(a_{s_{t-1}s_t}) + \ln(b_{s_t}(o_t))\right)$$

Le calcul repose sur le **score** $H(i,t)$ du meilleur chemin partiel aboutissant à l'état $i$ au temps $t$,

$$H(i,t) = \max_{s_1,\ldots,s_{t-1}} \ln \mathbb{P}[o_1,\ldots,o_t,s_1,\ldots,s_t=i]$$

et sur le **meilleur prédécesseur** $B(i,t)$ du nœud $(i,t)$. L'algorithme se déroule en trois phases.

**Initialisation** ($t = 1$) :

$$H(i,1) = \ln \pi_i + \ln b_i(o_1)$$

$$B(i,1) = 0.$$

**Propagation** (pour $t = 2, \ldots, T$ et $i = 1, \ldots, N$) :

$$H(i,t) = \ln b_i(o_t) + \max_j \left[ H(j,t-1) + \ln a_{ji} \right],$$

$$B(i,t) = \arg \max_j \left[ H(j,t-1) + \ln a_{ji} + \ln b_i(o_t) \right].$$

**Backtracking** :

$$H^* = \max_i H(i,T),$$

$$\hat{x}_t = B(\hat{x}_{t+1}, t+1) \quad \text{pour } t = T-1, \ldots, 1.$$

# Interprétation

Sur le treillis de la figure, quatre états numérotés de $1$ à $4$ se succèdent le long des transitions, et huit colonnes portent les observations $o_1, o_2, \ldots, o_8$. Des flèches partent de plusieurs cases d'une colonne et convergent vers une case de la colonne suivante, où elles portent l'étiquette « max » : le maximum se prend localement, case par case, sur les chemins partiels déjà construits.

À chaque nœud $(i,t)$, $H(i,t)$ est le score du meilleur chemin partiel jusqu'à ce nœud et $B(i,t)$ son meilleur prédécesseur : la propagation ne retient ainsi, à chaque nœud, que le meilleur chemin partiel. Une fois le treillis parcouru, $H^* = \max_i H(i,T)$ donne le score du meilleur chemin complet et le backtracking reconstruit la séquence d'états optimale en remontant les prédécesseurs mémorisés.

La conservation d'un seul chemin partiel par case rend l'exploration praticable : le nombre de chemins partiels retenus reste proportionnel au nombre de cases du treillis, alors que le nombre de chemins complets croît de façon exponentielle avec la longueur de la séquence.

# Exemple

**Viterbi en action.** Le [[Treillis|treillis]] comporte 4 états et 8 observations $o_1, \ldots, o_8$. Pour simplifier les calculs, on suppose

$$\ln(\pi_i) = -1 \quad \forall i$$

$$\ln(a_{ij}) = -1 \quad \forall i,j,$$

et les scores de base des cellules sont $H(i,t) = \ln b_i(o_t)$ :

| État | $o_1$ | $o_2$ | $o_3$ | $o_4$ | $o_5$ | $o_6$ | $o_7$ | $o_8$ |
|---|---|---|---|---|---|---|---|---|
| 1 | -3 | -3 | -2 | -2 | -1 | -2 | -1 | -1 |
| 2 | -2 | -2 | -3 | -3 | -3 | -2 | -1 | -1 |
| 3 | -1 | -1 | -2 | -2 | -2 | -2 | -2 | -1 |
| 4 | -1 | -2 | -1 | -1 | -2 | -3 | -3 | -3 |

Les premières étapes du calcul se déroulent pas à pas :

$$\begin{aligned}
H(1,1) &= \ln b_1(o_1) + \ln(\pi_1) = -(3 + 1) \\
H(2,1) &= \ln b_2(o_1) + \ln(\pi_2) = -(2 + 1) \\
H(1,2) &= \ln b_1(o_2) + \ln(a_{11}) + H(1,1) = -(3 + 1 + 4) \\
H(2,2) &= \max \begin{cases} \ln b_2(o_2) + \ln(a_{22}) + H(2,1) \\ \ln b_2(o_2) + \ln(a_{12}) + H(1,1) \end{cases} \\
H(3,2) &= \max \begin{cases} \ln b_3(o_2) + \ln(a_{13}) + H(1,1) \\ \ln b_3(o_2) + \ln(a_{23}) + H(2,1) \end{cases} \\
H(4,2) &= \ln b_4(o_2) + \ln(a_{24}) + H(2,1) \\
H(1,3) &= \ln b_1(o_3) + \ln(a_{11}) + H(1,2) \\
H(2,3) &= \max \begin{cases} \ln b_2(o_3) + \ln(a_{22}) + H(2,2) \\ \ln b_2(o_3) + \ln(a_{12}) + H(1,2) \end{cases} \\
H(3,3) &= \max \left\{ \begin{aligned} & \ln b_3(o_3) + \ln(a_{33}) + H(3,2) \\ & \ln b_3(o_3) + \ln(a_{23}) + H(2,2) \\ & \ln b_3(o_3) + \ln(a_{13}) + H(1,2) \end{aligned} \right. \\
H(4,3) &= \max \left\{ \begin{aligned} & \ln b_4(o_3) + \ln(a_{44}) + H(4,2) \\ & \ln b_4(o_3) + \ln(a_{34}) + H(3,2) \\ & \ln b_4(o_3) + \ln(a_{24}) + H(2,2) \end{aligned} \right.
\end{aligned}$$

Le calcul se poursuit de la même manière jusqu'au dernier pas $t = 8$ : le meilleur score global vaut $H^* = -23$, atteint pour $\hat{s}_8 = 3$. Le backtracking donne la séquence d'états optimale

$$S_1 = 2, \quad S_2 = 3, \quad S_3 = 3, \quad S_4 = 3, \quad S_5 = 3, \quad S_6 = 3, \quad S_7 = 3, \quad S_8 = 3.$$

# Remarque

- Le principe repose sur le [[Principe d'optimalité de Bellman|principe d'optimalité de Bellman]] : le meilleur chemin complet passant par une case contient le meilleur chemin partiel aboutissant à cette case, de sorte qu'écarter les autres chemins partiels de cette case ne fait perdre aucune solution optimale.
- L'exploration est complète au sens où toutes les cases du treillis sont visitées : aucune branche n'est élaguée au cours de la construction.
- La séquence restituée est optimale globalement, et non la suite des états les plus probables observation par observation : c'est la différence avec l'[[Algorithme forward]], qui somme sur tous les chemins au lieu de n'en retenir qu'un.
- Le même schéma de programmation dynamique s'applique à des scores de traits, sans probabilités de transition ni d'émission : voir la [[Programmation dynamique pour un champ aléatoire conditionnel]].

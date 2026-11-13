#dmv-sequence_mining

# Définition

Dans une [[Base de séquences]] $D$, une séquence $S$ supporte un [[Motif séquentiel]] $P$ si $P \subseteq S$ au sens de l'[[Inclusion de sous-séquence]].

Le support de $P$, noté $sup(P)$, est la proportion des séquences de $D$ qui supportent $P$ :

$$sup(P) = \frac{|\{S \in D \mid P \subseteq S\}|}{|D|}$$

Un motif séquentiel $P$ est fréquent si $sup(P) \ge minsup$, où $minsup$ est un seuil fixé.

# Exemple

Base de quatre séquences indexées par quatre dates, chaque case étant l'itemset d'une date :

| Séquence | $d_1$ | $d_2$ | $d_3$ | $d_4$ |
| :-- | :-- | :-- | :-- | :-- |
| $S_1$ | $(a\ b\ c)$ | $(b\ d\ e)$ | $(a\ b\ f)$ | $(a\ d)$ |
| $S_2$ | $(a\ b\ c)$ | $(a\ b\ c)$ |  | $(b\ c\ f)$ |
| $S_3$ | $(b\ c\ e)$ |  | $(a\ d\ f)$ | $(a\ b\ c)$ |
| $S_4$ | $(a\ c\ f)$ | $(b\ d)$ | $(a\ b\ f)$ | $(e)$ |

Calcul demandé : $sup(\langle(a\ c)(b)(b\ f)\rangle)$.

Calculs demandés pour les motifs suivants :

- $\langle(a)(b\ d)(a)\rangle$
- $\langle(b)(b)(f)\rangle$
- $\langle(b)(d)(f)\rangle$
- $\langle(c\ f)(b)\rangle$

Sous une [[Contrainte d'écart temporel|contrainte d'écart temporel]] fixée à $[0,1]$, le même calcul se mène sur une base horodatée de six dates :

| Séquence | $t=1$ | $t=2$ | $t=3$ | $t=4$ | $t=5$ | $t=6$ |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| $S_1$ | $(a\ b\ c)$ | $(b)$ | $(d\ e)$ | $(a\ f)$ | $(b)$ | $(a\ d)$ |
| $S_2$ | $(a\ b\ c)$ | $(b\ c)$ | $(a)$ | $(b\ c\ f)$ |  |  |
| $S_3$ | $(b\ c\ e)$ | $(a\ d\ f)$ | $(e)$ | $(a\ b\ c)$ | $(f)$ |  |
| $S_4$ | $(a\ c\ f)$ | $(b\ d)$ | $(a\ b\ f)$ | $(e)$ |  |  |

Les supports à calculer sont ceux des mêmes motifs, l'écart temporel autorisé entre deux itemsets consécutifs du motif modifiant les séquences qui le supportent.

# Remarque

Le support ne compte pas les occurrences multiples d'un motif dans une séquence : une séquence qui supporte le motif ne compte qu'une fois, quel que soit le nombre de façons dont le motif s'y plonge.

Le support décroît quand le motif s'allonge, ce qui donne l'[[Anti-monotonie du support des motifs séquentiels]] et fonde l'élagage de l'[[Énoncé du problème de fouille de motifs séquentiels|espace de recherche]].

La notion est l'analogue, pour les séquences, du [[Support d'un itemset]] ; pour les épisodes d'une séquence d'événements, la notion correspondante est la [[Fréquence d'un épisode]].

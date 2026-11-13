#dmv-sequence_mining

# Propriétés

Soit un [[Épisode|épisode]] $\alpha$ d'une [[Séquence d'événements|séquence d'événements]] $S$, une largeur de fenêtre $w$ et un seuil $min\_freq$.

Propriété d'anti-monotonie des épisodes : si $\alpha$ est [[Fréquence d'un épisode|fréquent]], alors tout sous-épisode $\beta \subseteq \alpha$ est fréquent.

$$fr(\alpha, S, w) \ge min\_freq \implies fr(\beta, S, w) \ge min\_freq$$

La fréquence ne peut donc pas augmenter quand l'épisode s'enrichit.

$$\beta \subseteq \alpha \implies fr(\beta, S, w) \ge fr(\alpha, S, w)$$

Toute fenêtre de $S$ dans laquelle $\alpha$ se produit est une fenêtre dans laquelle $\beta$ se produit aussi, puisque $\beta$ est une partie de $\alpha$ : l'ensemble des fenêtres comptées pour $\alpha$ est contenu dans celui des fenêtres comptées pour $\beta$. Les deux fréquences ont le même dénominateur, l'ensemble $W(S, w)$ des fenêtres de largeur $w$, d'où l'inégalité.

# Interprétation

La contraposée est la forme utile pour la recherche : si un sous-épisode $\beta$ n'est pas fréquent, aucun épisode $\alpha$ qui le contient ne peut l'être. Un tel épisode est donc écarté sans que sa fréquence soit comptée.

L'exploitation de cette propriété comme filtre des candidats est décrite dans l'[[Algorithme WINEPI]].

# Remarque

La propriété porte sur la relation d'inclusion entre épisodes. Elle ne dit rien de deux épisodes non comparables : leurs fréquences peuvent différer librement, l'un être fréquent et l'autre non.

Elle est l'analogue, pour les épisodes, de l'[[Anti-monotonie du support des motifs séquentiels]]. Les objets et la mesure diffèrent : ici l'inclusion est une inclusion d'épisodes, c'est-à-dire d'ensembles partiellement ordonnés de types d'événements, et la mesure est la proportion de fenêtres d'une séquence unique où l'épisode se produit ; là, l'inclusion est l'[[Inclusion de sous-séquence]] et la mesure est la proportion des séquences d'une base qui contiennent le motif.

#dmv-sequence_mining

# Définition

La fréquence d'un épisode $\alpha$ dans une séquence d'événements $S$, pour une largeur de fenêtre $w$, est la fraction des fenêtres de $S$ dans lesquelles l'épisode se produit :

$$fr(\alpha, S, w) = \frac{|\{S_w \in W(S, w) \mid \alpha \text{ se produit dans } S_w\}|}{|W(S, w)|}$$

où $W(S, w)$ est l'ensemble de toutes les fenêtres de $S$ de largeur $w$, au sens de la [[Fenêtre glissante de WINEPI]].

Un épisode $\alpha$ est fréquent si $fr(\alpha, S, w) \ge min\_freq$, où $min\_freq$ est un seuil fixé.

# Remarque

Si un épisode est fréquent, tous ses sous-épisodes $\beta \subseteq \alpha$ le sont aussi : la fréquence ne peut que décroître quand l'épisode s'enrichit, ce qui donne l'[[Anti-monotonie des épisodes]].

Le support d'un épisode désigne le même objet que sa fréquence : les deux noms sont employés indifféremment.

La fréquence se mesure ici sur des fenêtres glissantes. Une approche alternative, l'[[Algorithme MINEPI]], s'en passe entièrement : elle s'appuie directement sur les [[Occurrence minimale d'un épisode|occurrences minimales]] de chaque épisode, c'est-à-dire sur les intervalles où l'épisode se produit sans se produire dans un sous-intervalle strict.

La notion est l'analogue, pour les épisodes d'une séquence d'événements, du [[Support d'un motif séquentiel]] : même proportion de contextes où le motif apparaît, les fenêtres d'une séquence remplaçant les séquences d'une base.

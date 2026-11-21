#dmv-sequence_mining

# Définition

Soit un [[Épisode|épisode]] $\alpha$ et une [[Séquence d'événements|séquence d'événements]] $S$. Un intervalle $[t_s, t_e]$ est une occurrence minimale de $\alpha$ dans $S$ si les deux conditions suivantes sont réunies :

- $\alpha$ se produit dans la fenêtre correspondant à cet intervalle ;
- $\alpha$ ne se produit dans aucun sous-intervalle strict de cet intervalle.

L'ensemble des occurrences minimales de $\alpha$ dans $S$ se note $mo(\alpha)$ :

$$mo(\alpha) = \{[t_s, t_e] \mid [t_s, t_e] \text{ est une occurrence minimale de } \alpha\}$$

# Exemple

Dans une séquence $s$, un épisode $\beta$ composé des types d'événements $A$ et $B$ possède trois occurrences minimales :

$$mo(\beta) = \{[30, 40], [40, 60], [60, 70]\}$$

L'intervalle $[30, 70]$ contient $\beta$ mais n'est pas minimal : il renferme des sous-intervalles stricts dans lesquels $\beta$ se produit déjà.

Un épisode $\alpha$ formé de $A$ et $B$ en parallèle, tous deux suivis de $C$, possède pour sa part une seule occurrence minimale :

$$mo(\alpha) = \{[60, 80]\}$$

L'intervalle $[30, 80]$ n'est pas minimal, pour la même raison.

# Remarque

Cette notion se distingue du comptage par [[Fenêtre glissante de WINEPI|fenêtres glissantes]] qui sous-tend la [[Fréquence d'un épisode|fréquence d'un épisode]] ; elle sert de base à l'[[Algorithme MINEPI]], qui localise ainsi exactement les apparitions d'un épisode.

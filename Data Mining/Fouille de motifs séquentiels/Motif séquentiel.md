#dmv-sequence_mining

# Définition

Un **motif séquentiel** est une séquence $\langle X_1, \dots, X_n\rangle$ où chaque $X_i$ est un itemset.

# Exemple

Dans le motif séquentiel $\langle(a\ b)(c)(d\ e)\rangle$ :

- $a$ et $b$ sont synchrones : ils partagent le même horodatage ;
- $d$ et $e$ sont synchrones : ils partagent le même horodatage ;
- $c$ survient après $a$ et $b$ ;
- $d$ et $e$ surviennent après $c$.

# Remarque

Un motif séquentiel est donc un cas particulier de la séquence décrite dans [[Vocabulaire des motifs séquentiels]] : la séquence y est une suite d'itemsets, et c'est cette suite qui constitue le motif recherché.

Chaque composante $X_i$ du motif est un [[Items, itemsets et base de transactions|itemset]], c'est-à-dire un ensemble d'items sans ordre interne : les items d'un même $X_i$ sont simultanés, seul l'ordre des itemsets $X_1, \dots, X_n$ porte une information temporelle.

Le motif n'est pas observé directement : il est comparé aux séquences de la base par inclusion, ce qui conduit à la notion de [[Support d'un motif séquentiel|support]] et à celle de motif fréquent.

Un motif séquentiel est le cas particulier ordonné de l'[[Épisode|épisode]] : l'épisode autorise un ordre partiel entre ses événements, alors que le motif impose un ordre total entre ses itemsets.

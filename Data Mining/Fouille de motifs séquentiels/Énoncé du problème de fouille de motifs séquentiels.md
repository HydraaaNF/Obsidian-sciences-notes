#dmv-sequence_mining

# Définition

Étant donnés une [[Base de séquences]] $D$ et un seuil de support minimal $minsup$, le problème de la fouille de motifs séquentiels consiste à trouver l'ensemble de **toutes les sous-séquences fréquentes** de $D$ vis-à-vis de $minsup$.

En notant $sup(s)$ le [[Support d'un motif séquentiel|support]] d'une séquence $s$ dans $D$, l'ensemble demandé s'écrit :

$$\mathcal{F}(D, minsup) = \{ s \mid s \text{ est une sous-séquence d'une séquence de } D \text{ et } sup(s) \ge minsup \}$$

# Interprétation

Les entrées du problème sont la base de séquences et le seuil $minsup$ ; la sortie est un ensemble de [[Motif séquentiel|motifs séquentiels]], sans restriction sur leur longueur ni sur leur nombre.

Le problème porte sur l'ensemble complet des sous-séquences assez fréquentes, et non sur un motif particulier : l'énumérer conduit à l'[[Espace de recherche des motifs séquentiels]], que les [[Panorama des algorithmes de fouille de motifs séquentiels|algorithmes de fouille]] parcourent en élaguant les branches dont les motifs ne peuvent plus être fréquents.

# Remarque

L'énoncé est l'analogue, pour des séquences, de la recherche des [[Itemset fréquent|itemsets fréquents]] : mêmes entrées (une base, un seuil), même exigence d'exhaustivité, la structure des données changeant seule.

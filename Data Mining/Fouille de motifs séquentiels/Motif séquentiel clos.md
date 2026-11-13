#dmv-sequence_mining

# Définition

Soit un [[Motif séquentiel]] $s$ et un ensemble de motifs séquentiels $S$. Le motif $s$ est clos sur $S$ si et seulement si aucun motif de $S$ ne le contient strictement en gardant le même [[Support d'un motif séquentiel|support]] :

$$\nexists s' \in S \text{ tel que } s \subsetneq s' \text{ et } sup(s) = sup(s')$$

# Interprétation

Un motif clos est un motif que l'on ne peut pas allonger sans perdre du support : toutes ses sur-séquences présentes dans $S$ ont un support strictement inférieur.

Dans sa classe d'inclusion, il résume donc à lui seul les motifs de $S$ qu'il contient et qui ont le même support ; deux motifs incomparables peuvent partager un support sans que l'un résume l'autre.

# Remarque

Tout motif est contenu dans lui-même : avec une inclusion non stricte, chaque motif de $S$ serait son propre témoin et aucun motif ne pourrait être clos. La condition de clôture porte donc bien sur une inclusion stricte.

Tout [[Motif séquentiel maximal]] est clos : s'il n'existe aucune sur-séquence de $s$ dans $S$, il n'en existe en particulier aucune de même support.

La réciproque est fausse : un motif clos peut avoir des sur-séquences dans $S$, à condition que leur support soit strictement plus faible. Les motifs clos sont donc au moins aussi nombreux que les motifs maximaux, et strictement plus nombreux dès qu'un motif clos admet une sur-séquence dans $S$.

Les motifs clos s'obtiennent de deux façons :

- en post-traitement, en filtrant les motifs fréquents déjà extraits ;
- directement, avec un algorithme dédié comme [[Algorithme CloSpan]] ou BIDE, conçu pour ne conserver que les motifs clos.

Les motifs maximaux se déduisent ensuite des motifs clos par un filtrage supplémentaire.

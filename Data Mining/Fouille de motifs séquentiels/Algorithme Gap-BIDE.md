#dmv-sequence_mining

# Algorithme

Gap-BIDE étend BIDE, algorithme de fouille des [[Motif séquentiel clos|motifs séquentiels clos]], à la fouille sous [[Contrainte d'écart temporel|contrainte d'écart maximal]] : seule l'étape d'élagage des candidats est modifiée, et elle s'appuie sur la notion de [[Sous-séquence contiguë]].

# Propriétés

L'élagage d'un $k$-candidat se décrit selon que la contrainte d'écart maximal est imposée ou non.

- Sans contrainte d'écart maximal : un $k$-candidat est élagué si au moins une de ses $(k-1)$-sous-séquences est infréquente.
- Avec contrainte d'écart maximal : un $k$-candidat est élagué si au moins une de ses $(k-1)$-sous-séquences contiguës est infréquente.

Le contrôle porte donc, sans contrainte, sur toutes les $(k-1)$-sous-séquences du candidat, et avec la contrainte, sur les seules sous-séquences contiguës.

# Exemple

Pour le candidat $\langle (b)\ (c)\ (e) \rangle$, les deux sous-séquences contiguës de longueur 2 sont vérifiées :

- $\langle (b)\ (c) \rangle$
- $\langle (c)\ (e) \rangle$

# Remarque

Sous contrainte d'écart maximal, l'[[Anti-monotonie du support des motifs séquentiels|anti-monotonie du support]] ne vaut plus pour toutes les sous-séquences d'un motif, comme le montre le [[Contre-exemple à l'anti-monotonie sous contrainte d'écart maximal]] : Gap-BIDE restreint de ce fait le contrôle d'infréquence aux sous-séquences contiguës.

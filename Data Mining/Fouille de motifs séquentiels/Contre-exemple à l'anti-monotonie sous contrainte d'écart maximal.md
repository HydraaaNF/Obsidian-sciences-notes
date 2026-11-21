#dmv-sequence_mining

# Exemple

Soit la [[Base de séquences]] suivante, numérotée par identifiant de séquence :

- séquence 10 : $\langle(abd)(bc)(e)\rangle$
- séquence 20 : $\langle(ab)(bcd)\rangle$
- séquence 30 : $\langle(ab)(bcd)(bde)\rangle$
- séquence 40 : $\langle(b)(c)(d)(de)\rangle$
- séquence 50 : $\langle(ac)(bde)\rangle$

On impose une [[Contrainte d'écart temporel|contrainte d'écart maximal]] $maxgap = 1$ et un seuil de fréquence $minsup = 50\,\%$.

Les supports des deux motifs suivants s'écartent alors du sens imposé par l'[[Inclusion de sous-séquence]] :

- $sup(\langle(b)(e)\rangle) = 40\,\%$, le motif est porté par les séquences 10 et 30 ;
- $sup(\langle(b)(c)(e)\rangle) = 60\,\%$, le motif est porté par les séquences 10, 30 et 40.

Le motif long $\langle(b)(c)(e)\rangle$ contient le motif court $\langle(b)(e)\rangle$, et pourtant son [[Support d'un motif séquentiel|support]] lui est supérieur.

# Interprétation

Avec $maxgap = 1$, la séquence 40 supporte $\langle(b)(c)(e)\rangle$ : les itemsets $b$, $c$ et $e$ y sont assez rapprochés pour que chacun des écarts successifs respecte la contrainte.

Elle ne supporte pas $\langle(b)(e)\rangle$ : privé de l'itemset $c$, le motif met en regard les itemsets $b$ et $e$ de cette séquence, dont l'écart dépasse $maxgap$.

La contrainte s'évalue donc occurrence par occurrence, et non globalement sur la séquence : allonger un motif peut créer de nouvelles occurrences contraintes, en rapprochant des itemsets que le motif court laissait éloignés.

Le motif court n'est pas fréquent ($40\,\% < 50\,\%$) alors que son sur-motif l'est ($60\,\% \ge 50\,\%$) : l'[[Anti-monotonie du support des motifs séquentiels|anti-monotonie du support]] tombe.

# Remarque

Le contre-exemple tient à la contrainte d'écart maximal elle-même, et non à la base de séquences : si $maxgap$ est infini, la séquence 40 supporte aussi $\langle(b)(e)\rangle$, dont le support remonte à $60\,\%$ et redevient au moins égal à celui du motif long.

Dès qu'une borne supérieure d'écart est imposée, l'élagage d'un candidat ne peut plus porter que sur ses sous-séquences contiguës de taille immédiatement inférieure : un candidat $k$-séquence est écarté si l'une de ses sous-séquences contiguës de taille $k-1$ n'est pas fréquente. L'infréquence d'un motif court ne garantit donc plus celle de toutes ses extensions : l'inférence ne vaut plus que lorsque ce motif est une sous-séquence contiguë de l'extension. C'est la difficulté que doit traiter un algorithme dédié comme [[Algorithme Gap-BIDE]].

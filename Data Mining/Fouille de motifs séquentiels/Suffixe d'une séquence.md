#dmv-sequence_mining

# Définition

Soient $S=\langle I_1,\dots,I_n\rangle$ une séquence et $S'=\langle I'_1,\dots,I'_m\rangle$ une [[Inclusion de sous-séquence|sous-séquence]] de $S$.

La séquence $S''=\langle J_o,\dots,J_n\rangle$ est un **suffixe** de $S$ par rapport à $S'$ si :

- $\langle I_1,\dots,I_o\rangle$ est le plus petit préfixe contenant $S'$,
- tous les items de $(J_o - I'_m)$ sont ordonnés après l'élément de $I'_m$ dans $I_o$.

# Exemple

Sur la séquence

$$S = \langle(a)(abc)(ac)(d)(cf)\rangle$$

le suffixe par rapport à la sous-séquence $\langle a\rangle$ est la fin de $S$ qui suit le plus petit préfixe contenant celle-ci :

$$\text{Suffix}(\langle a\rangle) = \langle(abc)(ac)(d)(cf)\rangle$$

Le suffixe par rapport à $\langle(a)(b)\rangle$ conserve en outre l'item $c$ de l'itemset $(abc)$, seul item de cet itemset ordonné après l'élément $b$ :

$$\text{Suffix}(\langle(a)(b)\rangle) = \langle(c)(ac)(d)(cf)\rangle$$

# Remarque

Le suffixe n'est pas attaché à une séquence seule : il se définit relativement à une sous-séquence $S'$ donnée, et dépend donc à la fois de $S$ et de $S'$.

Le plus petit préfixe $\langle I_1,\dots,I_o\rangle$ s'arrête à l'itemset $I_o$ où se termine l'occurrence de $S'$. La seconde condition règle le cas où cette occurrence se termine à l'intérieur de $I_o$ : seuls les items de $I_o$ placés après l'élément de $I'_m$ subsistent dans $J_o$, ce qui explique l'itemset $(c)$ de l'exemple précédent.

Le couple formé du plus petit préfixe contenant $S'$ et du suffixe correspondant partage la séquence en deux segments. C'est ce partage que le calcul des [[Base projetée|bases projetées]] de l'[[Algorithme PrefixSpan]] exploite pour ne développer que les prolongements d'un préfixe fréquent, au lieu de parcourir tout l'[[Espace de recherche des motifs séquentiels|espace de recherche]] des [[Motif séquentiel|motifs séquentiels]].

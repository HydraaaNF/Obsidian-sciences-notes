## Définition
Soit $\Sigma$ un [[Alphabet|alphabet]]. Les langages rationnels sont définis par :
1. $\{\epsilon\}$ et $\emptyset$ sont des langages rationnels
2. $\forall a \in \Sigma, \{a\}$ est un langage rationnel
3. Si $L_1$ et $L_2$ sont des langages rationnels, alors $L_1 \cup L_2$, $L_1L_2$ et $L_1^*$ sont des langages rationnels

## Remarques
- Tous les langages finis sont rationnels.
- Par définition, l’ensemble des langages rationnels est clos pour les trois opérations rationnelles.
- La famille des langages rationnels correspond au plus petit ensemble de langages qui contient tous les langages finis et rationnellement clos.

## Exemples
- $\{a^nb^n|n\geq 0\}$ n'est pas un langage rationnel
- $\{a^mb^n|m \geq 0, n \geq 0\}$ est un langage rationnel
- $\{0, 1\}^*\{111\}\{0, 1\}^*$ est un langage rationnel
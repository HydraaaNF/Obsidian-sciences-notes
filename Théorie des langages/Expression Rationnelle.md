## Définition
Soit $\Sigma$ un [[Alphabet|alphabet]]. Les expressions rationnelles sur $\Sigma$ sont définies inductivement par :
1. $\epsilon$ et $\emptyset$ sont des expressions rationnelles
2. $\forall a \in \Sigma, a$ est une expression rationnelle
3. si $e_1$ et $e_2$ sont des expressions rationnelles, alors $(e_1 + e_2)$, $(e_1e_2)$ et $(e_1^*)$ sont des expressions rationnelles
Une expression rationnelle est toute formule construite par un nombre fini d’applications de la récurrence (3).

### Lien avec les langages rationnels
1. $\epsilon$ dénote le langage $\{\epsilon\}$ et $\emptyset$ dénote le langage vide
2. $\forall a \in \Sigma, a$ dénote le langage $\{a\}$
3. $(e_1+e_2)$ dénote l'union des langages dénotés par $e_1$ et $e_2$
4. $(e_1e_2)$ dénote la concaténation des langages dénotés par $e_1$ et $e_2$
5. $(e_1^*)$ dénote la fermeture de Kleene du langage dénoté par $e_1$

### Règles de priorité
1. étoile de Kleene, concaténation, union
2. opérateurs binaires pris associatifs à gauche

### Équivalences élémentaires
- $\emptyset e = e \emptyset = \emptyset$
- $\emptyset^* = \epsilon$
- $e+f = f+e$
- $e+e=e$
- $e(f+g) = ef + eg$
- $(ef)^*e = e(fe)^*$
- $(e+f)^* = e^*(e+f)^*$
- $(e+f)^* = (e^*f^*)^*$
- $\epsilon e = e \epsilon = e$
- $\epsilon^* = \epsilon$
- $e + \emptyset = e$
- $e^* = (e^*)^*$
- $(e+f)g = eg + fg$
- $(e+f)^* = (e^* + f)^*$
- $(e + f)^* = (e^*f)^*e^*$

### Exemple
- $bb^*(a^*b^* + \epsilon)b = b(b^*a^* + \epsilon)bb^*$

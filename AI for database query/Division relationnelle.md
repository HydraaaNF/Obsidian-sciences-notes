# Définition
Soit $r$ une relation de schéma $R(X, A)$ et $s$ une relation de schéma $S(Y, B)$, avec $A$ et $B$ compatibles (même domaine). La **division** de $r$ par $s$ est :

$$
r[A \div B]s = \{x \mid \forall a \in s[B],\ (x, a) \in r\}
$$

C'est l'ensemble des $x$ associés, dans $r$, à toutes les valeurs de $B$ présentes dans $s$.

# Propriétés
Formulation équivalente, avec $\Omega_r(x) = \{a \mid \langle x, a \rangle \in r\}$ :

$$
r[A \div B]s = \{x \mid s[B] \subset \Omega_r(x)\}
$$

# Exemple
$\text{Commandes}$ :

| \#c | \#p | qté |
| --- | --- | --- |
| c1 | p1 | 100 |
| c2 | p2 | 50 |
| c1 | p3 | 70 |
| c3 | p1 | 80 |
| c3 | p2 | 50 |
| c3 | p4 | 20 |

$\text{ProduitsVerts}$ :

| \#p | nom |
| --- | --- |
| p1 | … |
| p2 | … |

Requête : les clients qui ont commandé tous les produits verts.

$$
\text{Commandes}[\#c, \#p]\ [\#p \div \#p]\ \text{ProduitsVerts}
$$

Résultat : $\{c3\}$.

# Remarque
Version pour les relations floues : [[Division de relations floues]]. Expressions en SQL : [[Division en SQL]].

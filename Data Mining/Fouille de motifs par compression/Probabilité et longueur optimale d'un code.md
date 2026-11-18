#dmv-pattern_mining_with_information_theory
# Définition

Soit $D$ une base de transactions et $CT$ une [[Table de codes]]. Pour une entrée $j$ de $CT$, l'usage de $j$ compte le nombre de transactions $t$ de $D$ dont le [[Couverture d'une transaction par une table de codes|cover]] contient $j$ :

$$usage(j) = \left|\{t \in D \mid j \in cover(t, CT)\}\right|$$

La probabilité affectée à $c$ par la table de codes est son usage rapporté à la somme des usages de toutes les entrées de $CT$ :

$$P(c \mid CT) = \frac{usage(c)}{\sum_{i \in CT} usage(i)}$$

# Propriétés

Le code optimal pour la distribution de probabilité $P$ attribue à l'entrée $c \in CT$ un code de longueur

$$L(c \mid CT) = -\log P(c \mid CT)$$

la longueur étant exprimée en bits, donc avec le logarithme de base $2$ : une entrée d'autant plus souvent utilisée reçoit un code d'autant plus court.

# Exemple

Table de codes de huit entrées, avec leurs usages et leurs longueurs de code :

| Itemset | Usage | $P(c \mid CT)$ | $L(c \mid CT)$ (bits) |
| --- | --- | --- | --- |
| {A, C} | 3 | 3/13 | 2,12 |
| {B, D} | 3 | 3/13 | 2,12 |
| {C, E} | 2 | 2/13 | 2,70 |
| {A} | 1 | 1/13 | 3,70 |
| {B} | 2 | 2/13 | 2,70 |
| {C} | 0 | 0 | aucun code |
| {D} | 1 | 1/13 | 3,70 |
| {E} | 1 | 1/13 | 3,70 |

La somme des usages vaut $3 + 3 + 2 + 1 + 2 + 0 + 1 + 1 = 13$, d'où $P(\{A, C\}) = 3/13$ et $L(\{A, C\}) = -\log(3/13) \approx 2{,}12$ bits. L'entrée $\{C\}$, d'usage nul, ne reçoit aucun code : elle n'est jamais utilisée pour encoder les données.

Les longueurs obtenues, reportées en largeur de barre :

```chart
type: bar
labels: ["{A, C}", "{B, D}", "{C, E}", "{A}", "{B}", "{D}", "{E}"]
series:
  - title: Longueur du code (bits)
    data: [2.12, 2.12, 2.70, 3.70, 2.70, 3.70, 3.70]
```

# Remarque

Les longueurs de code sont optimales au sens de la théorie de l'information : aucune distribution de codes ne peut faire mieux en moyenne sur cette distribution $P$, et la longueur moyenne est alors l'entropie de $P$.

Une entrée d'usage nul n'entre pour rien dans la somme des usages et ne reçoit pas de code ; c'est ce qui permet de mesurer la [[Longueur de description d'une table de codes]] sans compter les entrées inutilisées, et donc de chercher des tables plus petites que la [[Table de codes standard]].

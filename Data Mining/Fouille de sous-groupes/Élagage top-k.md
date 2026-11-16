#dmv-subgroup_discovery

# Définition

L'élagage top-k est un principe d'élagage d'une recherche exhaustive dans l'[[Espace de recherche des sous-groupes|espace des sous-groupes]]. La recherche ne vise pas l'énumération de tous les motifs : elle sort les $k$ sous-groupes de meilleure qualité, rangés par qualité décroissante, et abandonne en cours de route les branches qui ne peuvent plus entrer dans ce classement.

Il s'appuie sur une [[Estimation optimiste d'une fonction de qualité|estimation optimiste]] de la [[Fonction de qualité d'un sous-groupe|fonction de qualité]] : une fonction $oe$ qui majore strictement, pour tout motif $P$, la qualité de tous les raffinements de $P$. Pour de nombreuses fonctions de qualité, une telle estimation existe.

# Propriété

Soit $q$ la fonction de qualité et $P$, $P'$ deux motifs tels que $P'$ raffine $P$. L'estimation optimiste vérifie :

$$P' \supset P \implies oe(P) > q(P')$$

Aucun raffinement de $P$ ne peut donc dépasser la qualité $oe(P)$.

En situation top-k, on note $q_k$ la qualité du pire motif du top-k courant. Si l'estimation optimiste d'un motif $P$ d'une branche passe sous ce seuil, la branche peut être abandonnée :

$$oe(P) < q_k \implies \text{branche abandonnée}$$

# Algorithme

La recherche descend dans l'espace des motifs et tient à jour le top-k courant, trié par qualité décroissante ; elle n'ouvre les raffinements d'un motif que tant que sa borne ne le condamne pas.

```text
Entrée : espace de recherche, qualité q, estimation optimiste oe, entier k
T = ∅                                  // top-k courant, qualité décroissante
empiler le motif racine de l'espace
tant que la pile n'est pas vide :
    P = dépiler()
    si |T| < k ou q(P) > q_k :
        insérer P dans T, trié par qualité décroissante
        si |T| > k : retirer le pire motif de T
    si |T| = k et oe(P) < q_k :
        abandonner la branche issue de P
    sinon :
        empiler les raffinements de P
retourner T
```

# Remarque

L'[[Algorithme Apriori]] émonde le [[Treillis des itemsets|treillis des itemsets]] par la [[Propriété d'anti-monotonie du support|anti-monotonie du support]] : un itemset dont le support passe sous $minsup$ n'a aucun sur-ensemble fréquent, et sa descendance n'est jamais construite. L'élagage top-k applique le même principe à la qualité au lieu du support, avec une différence de seuil : Apriori compare à une fréquence minimale fixée à l'avance, l'élagage top-k compare à la qualité du pire motif du top-k courant, qui n'est connue qu'en cours de recherche.

Le seuil $q_k$ dépend de ce qui a déjà été trouvé : tant que moins de $k$ motifs sont retenus, aucune branche ne peut être écartée par ce critère, et le seuil ne peut que croître au fil de la recherche, si bien que l'élagage se resserre à mesure que le top-k se remplit.

Le classement produit est un classement par qualité seule, dont les défauts sont ceux du [[Limites du classement top-k|classement top-k]]. La place de ce principe parmi les stratégies d'exploration est décrite dans la [[Recherche des sous-groupes]].

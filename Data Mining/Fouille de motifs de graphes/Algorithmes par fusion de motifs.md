#dmv-graph_mining

# Définition

Deux motifs de taille $k$ sont compatibles lorsqu'ils partagent un noyau commun de taille $k-1$, c'est-à-dire lorsqu'ils ne diffèrent que par un élément.

# Algorithme

La génération repose sur une condition nécessaire de fréquence : si la mesure de support est [[Anti-monotonie du support dans une collection de graphes|anti-monotone]], pour qu'un $k$-motif soit fréquent, tous les $(k-1)$-motifs qu'il contient doivent être fréquents.

```
L₁ ← ensemble des 1-motifs fréquents
k ← 1
tant que L_k ≠ ∅ :
    C_{k+1} ← fusions des k-motifs compatibles de L_k
    élaguer C_{k+1} : ne conserver que les candidats dont tous les (k-1)-motifs sont fréquents
    L_{k+1} ← {c ∈ C_{k+1} | support(c) ≥ min_sup}
    k ← k + 1
retourner L₁ ∪ L₂ ∪ …
```

Chaque tour produit l'ensemble des motifs fréquents d'une taille de plus, et la boucle s'arrête dès qu'aucun motif de la taille courante n'est fréquent.

# Propriétés

Le déroulé est celui d'[[Algorithme Apriori|Apriori]], transposé aux motifs de graphes, mais chaque étape y change de coût :

- la génération des candidats exige, pour savoir si deux motifs peuvent être joints, de tester l'[[Isomorphisme de graphes|isomorphisme de graphes]] ;
- l'élagage exige le même test, pour vérifier que tous les $(k-1)$-motifs d'un candidat sont fréquents ;
- le comptage du support exige un test d'[[Isomorphisme de sous-graphe|isomorphisme de sous-graphe]] pour chaque candidat et chaque donnée.

# Remarque

Les principaux algorithmes de cette famille sont AGM et AcGM, [[Algorithme FSG|FSG]], FFSM, SPIN et DPMine. Leur principale différence tient à la définition du $k$-motif :

- $k$ sommets ;
- $k$ arêtes ;
- $k$ chemins arête-disjoints.

Le test d'isomorphisme de sous-graphe étant NP-complet, ce coût pèse sur toute la famille et motive les [[Code canonique d'un graphe|codes canoniques]], qui identifient un motif sans comparaison exhaustive, ainsi que l'approche par [[Croissance de motifs de graphes|croissance de motifs]], qui évite la fusion de motifs.

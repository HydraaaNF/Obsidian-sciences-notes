#dmv-graph_mining

# Définition

Dans FSG, un $k$-subgraph est un sous-graphe à $k$ arêtes : la taille d'un motif se mesure en nombre d'arêtes, et non en nombre de sommets.

# Exemple

Un triangle est un 3-subgraph, une chaîne de deux arêtes un 2-subgraph, un carré muni d'une diagonale un 5-subgraph. Le nombre de sommets n'entre pas dans cette numérotation : un triangle compte 3 arêtes pour 3 sommets, une étoile à 3 branches compte 3 arêtes pour 4 sommets.

# Algorithme

```
F₁ ← {1-subgraphes et 2-subgraphes fréquents, avec leurs comptes}    (balayage des transactions)
k ← 3
tant que F_{k-1} ≠ ∅ :
    C_k ← génération des candidats k-subgraphes à partir de F_{k-1}
    élaguer C_k : condition nécessaire, chacun des (k-1)-subgraphes d'un candidat est fréquent
    compter les occurrences des candidats par balayage de la base de graphes
    F_k ← {c ∈ C_k | compte(c) ≥ min_sup}
    k ← k + 1
retourner F₁ ∪ F₂ ∪ … ∪ F_k
```

L'initialisation isole les 1-subgraphes et les 2-subgraphes : leurs comptes sont obtenus par un premier balayage des transactions, et la boucle de génération ne démarre qu'à $k=3$.

# Remarque

FSG est un cas particulier des [[Algorithmes par fusion de motifs]] : les candidats d'une taille sont obtenus en fusionnant des motifs fréquents de la taille précédente, puis élagués par la condition que tous leurs $(k-1)$-subgraphes soient fréquents.

Le comptage s'appuie sur le [[Support d'un motif dans une collection de graphes|support dans une collection de graphes]], et chaque essai d'un candidat dans une transaction est un test d'[[Isomorphisme de sous-graphe|isomorphisme de sous-graphe]], donc un problème NP-complet.

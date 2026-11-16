#dmv-graph_mining

# Définition

Les données d'entrée de la découverte de sous-graphes fréquents relèvent de deux familles.

- Une **collection de graphes** : un ensemble, généralement grand, de graphes généralement petits. Exemples : des molécules, des phrases.
- Un **graphe unique** : un seul graphe, généralement grand. Exemples : le web sémantique, les réseaux sociaux, une molécule d'ADN.

# Remarque

La distinction n'est pas cosmétique : elle fixe la définition du [[Support d'un motif de graphe|support]], donc la mesure qui décide de la fréquence d'un motif.

- Dans une collection, le support se rapporte au nombre de graphes qui contiennent le motif, voir [[Support d'un motif dans une collection de graphes]].
- Sur un graphe unique, les occurrences se comptent à l'intérieur du même graphe, où elles se chevauchent, ce qui conduit aux mesures décrites dans [[Support naïf par comptage d'occurrences]], [[Support par chevauchement]] et [[Support par image minimale]].

Les deux familles se distinguent visuellement par l'échelle : d'un côté une poignée de petits graphes orientés et étiquetés sur les arêtes, de l'autre un graphe massif dont les sommets se comptent par centaines. Le coût de la fouille se lit donc à deux échelles différentes, le nombre de graphes dans un cas, le nombre d'occurrences dans un graphe dans l'autre.

Une collection de graphes se traite comme une [[Items, itemsets et base de transactions|base de transactions]] dont chaque transaction serait un graphe, alors qu'un graphe unique impose de travailler sur les seules occurrences internes.

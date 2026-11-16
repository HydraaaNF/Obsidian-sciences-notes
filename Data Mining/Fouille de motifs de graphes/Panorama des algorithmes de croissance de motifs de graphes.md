#dmv-graph_mining

# Interprétation

La [[Croissance de motifs de graphes]] désigne le fait de partir de motifs simples et de les étendre par ajout de sommets ou d'arêtes jusqu'à épuisement des motifs fréquents. Quatre algorithmes se distinguent par le nombre de citations :

- MoFa : conçu pour trouver des sous-structures dans des collections de molécules ; il génère plusieurs fois le même motif, ce qui en fait le moins efficace des quatre.
- gSpan : le plus cité ; il évite les générations multiples du même motif par étiquetage canonique, c'est-à-dire par un [[Code canonique d'un graphe]], et par une expansion en profondeur d'abord qui développe le chemin le plus à droite.
- FFSM : il combine l'expansion de motifs et une opération de jointure particulièrement efficace.
- Gaston : il travaille par phases pour éviter autant que possible l'isomorphisme de sous-graphe ; il part des motifs les plus simples (les chemins), s'en sert pour fouiller des motifs un peu plus complexes (les arbres), puis les graphes ; c'est le plus rapide des quatre.

# Remarque

Les quatre algorithmes visent le même objectif : ne produire chaque motif qu'une seule fois, malgré les nombreux chemins de recherche qui y mènent. Les deux leviers employés sont une stratégie de génération qui limite les doublons et la détection d'un motif déjà atteint par un autre chemin, ce que permet un [[Code canonique d'un graphe]]. Le classement ci-dessus porte sur la fréquence de citation, pas sur la seule rapidité : MoFa est le moins efficace et Gaston le plus rapide, alors que gSpan est le plus cité.

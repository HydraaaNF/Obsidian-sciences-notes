#dmv-pattern_mining_vs_deep_learning

# Définition

Les données de polymorphismes nucléotidiques simples (en anglais Single Nucleotide Polymorphism, SNP) sont un jeu de données de fouille de motifs de grande dimension : de 100 000 à 1 000 000 d'items, et dense.

# Interprétation

Miner de telles données est un problème de fouille de motifs particulièrement intéressant : le jeu compte de l'ordre de $10^5$ à $10^6$ items et il est dense.
La recherche d'un ensemble de motifs y est néanmoins difficile : les algorithmes de l'état de l'art ne passent pas du tout à l'échelle sur des données SNP (voir [[Complexité de la recherche d'un ensemble de motifs]]).
Cela motive d'explorer si un réseau de neurones, dont les méthodes savent traiter des millions d'attributs, peut trouver un bon ensemble de motifs sur de telles données, la question restant ouverte (voir [[Passage à l'échelle de l'apprentissage de motifs]]).

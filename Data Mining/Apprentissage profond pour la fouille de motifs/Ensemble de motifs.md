#dmv-pattern_mining_vs_deep_learning

# Définition

Un **ensemble de motifs** (en anglais *pattern set*) est un petit ensemble de motifs qui capture les structures principales existant dans les données.

# Interprétation

L'ensemble est qualifié de petit, et c'est la collection entière qui doit capturer les structures principales des données.

Chaque motif de l'ensemble se juge par rapport aux autres et non isolément, à la différence d'un [[Itemset fréquent]] retenu pour son seul support.

Trouver un ensemble de motifs est le problème de l'état de l'art en pattern mining.

# Remarque

L'apprentissage automatique offre une autre voie pour obtenir un tel ensemble, en apprenant directement les motifs qui le composent : voir [[Capture de motifs par l'apprentissage automatique]].

Les approches par compression construisent un tel ensemble sans l'apprendre : elles sélectionnent, dans un langage de motifs donné, le petit ensemble qui décrit le mieux les données, comme le montre le [[Panorama des approches par compression en fouille de motifs]].

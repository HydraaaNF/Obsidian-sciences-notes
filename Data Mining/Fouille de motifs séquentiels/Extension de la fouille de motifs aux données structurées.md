#dmv-sequence_mining

# Définition

Un **motif** est une régularité locale présente dans les données.

Un **itemset fréquent** est une régularité de données transactionnelles, c'est-à-dire de données décrites comme des ensembles d'éléments (voir [[Itemset fréquent]]).

# Interprétation

Les données ne se réduisent pas aux ensembles. Elles peuvent être de nombreux autres types : séquences, arbres, graphes, intervalles. Ces formes sont plus structurées qu'un ensemble, en ce que les éléments y entretiennent davantage de relations entre eux, et elles présentent elles aussi des régularités.

La fouille de motifs doit donc être étendue des données ensemblistes aux données structurées : il faut y définir ce qu'est un motif et comment l'identifier, ce qui est l'objet de l'[[Identification de motif dans des données structurées]].

# Remarque

L'extension à ces données soulève des questions propres, traitées séparément : comment repérer une occurrence d'un motif dans une structure, puis compter son support lorsque les occurrences se chevauchent ([[Chevauchement des occurrences et comptage du support]]), et quel coût la fouille y acquiert ([[Complexité de la fouille sur des données structurées]]).

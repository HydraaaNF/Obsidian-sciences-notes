#dmv-sequence_mining

# Définition

Les algorithmes de fouille de motifs séquentiels se rangent en trois familles.

**Algorithmes fondés sur Apriori**, aussi appelés générer et élaguer :

- format de données horizontal :
    - [[Algorithme GSP|GSP]], qui indexe les candidats dans un arbre de hachage ;
    - PSP, qui les range dans un arbre de préfixes et consomme moins de mémoire ;
- format de données vertical :
    - [[Algorithme SPADE|SPADE]] ;
    - SPAM ;
    - LAPIN-SPAM.

**Algorithmes de croissance de motifs** :

- FreeSpan ;
- [[Algorithme PrefixSpan|PrefixSpan]].

**Extensions** :

- fermeture :
    - [[Algorithme CloSpan|CloSpan]] ;
    - BIDE ;
    - [[Algorithme Gap-BIDE|Gap-BIDE]] ;
    - Clasp ;
- fouille d'épisodes :
    - [[Algorithme MINEPI|MINEPI]] ;
    - [[Algorithme WINEPI|WINEPI]] ;
- contraintes :
    - SPIRIT ;
    - SDMC.

# Interprétation

Le classement suit deux axes.

Le premier sépare les stratégies d'énumération : les algorithmes fondés sur Apriori engendrent des candidats puis les élaguent, tandis que les algorithmes de croissance de motifs construisent les motifs par extension successive sans passer par une génération explicite de candidats.

Le second, interne à la première famille, porte sur le format des données : le format horizontal range chaque séquence comme une suite d'itemsets, le format vertical associe à chaque item la liste des séquences où il apparaît.

Les extensions ne changent pas la stratégie d'énumération : elles restreignent l'ensemble des motifs retenus, soit par une condition de fermeture, soit par la forme du motif cherché ([[Épisode|épisodes]]), soit par des contraintes supplémentaires.

# Remarque

Plusieurs algorithmes du panorama ne sont cités que par leur nom : PSP, SPAM, LAPIN-SPAM, FreeSpan, BIDE, Clasp, SPIRIT et SDMC.

Le panorama ne fixe pas le choix d'un algorithme : [[Algorithme GSP|GSP]] et [[Algorithme PrefixSpan|PrefixSpan]] répondent au même [[Énoncé du problème de fouille de motifs séquentiels|problème de fouille]] et ne diffèrent que par le coût de l'énumération.

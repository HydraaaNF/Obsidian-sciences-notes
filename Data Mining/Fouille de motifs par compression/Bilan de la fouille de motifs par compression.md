#dmv-pattern_mining_with_information_theory

# Interprétation

La [[Principe de la longueur minimale de description|longueur minimale de description]] est un bon critère pour retenir des motifs importants et utiles : au lieu d'énumérer tous les motifs qui satisfont un jeu de contraintes (voir [[Énoncé standard de la fouille de motifs]]), on garde ceux dont la présence raccourcit la description des données.

# Propriétés

- Les algorithmes par compression approchent très bien l'idéal de la longueur minimale de description.
- Le nombre d'itemsets retenus est réduit de façon considérable.
- Le principe se transpose également à d'autres types de motifs : itemsets, séquences, flux.
- Les [[Motif comme propriété locale des données|motifs locaux]] et la théorie de l'information induisent naturellement de bons classifieurs, de bons algorithmes de clustering et de bonnes mesures de distance.
- Ces constructions fournissent une caractérisation et une explication immédiates des données.
- Elles ne demandent aucun paramètre explicite.

# Remarque

Le bilan porte sur trois réalisations concrètes, une par type de données traité :

- les itemsets avec [[Algorithme KRIMP|KRIMP]], complété par [[Algorithme SLIM|SLIM]] pour la construction progressive ;
- les séquences avec SQS, dont la [[Table de codes pour séquences d'événements|table de codes]] ajoute le codage des trous entre positions couvertes ;
- les graphes avec [[Compression d'un graphe par un ensemble de motifs|GraphMDL]] et sa [[Version progressive de GraphMDL|variante progressive]].

Les trois reposent sur le même arbitrage : un modèle court dont l'encodage des données est également court, mesuré par la [[Taille totale d'un modèle et des données encodées|taille totale]] de la description. Les objets produits ne servent pas qu'à compresser : voir [[Applications des tables de codes]].

La portée du critère se résume par la suite de questions à poser pour concevoir une nouvelle approche : voir [[Trois questions de conception d'une approche par compression]].

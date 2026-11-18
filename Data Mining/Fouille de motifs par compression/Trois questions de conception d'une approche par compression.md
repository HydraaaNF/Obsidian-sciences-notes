#dmv-pattern_mining_with_information_theory

# Interprétation

Appliquer la [[Principe de la longueur minimale de description|longueur minimale de description]] à la fouille de motifs se ramène à trois questions de conception, chacune relevant d'une discipline distincte :

- **Quel type de modèle utiliser ?** C'est une question de modélisation des données : le modèle prend la forme d'un ensemble de motifs muni d'un encodage, et cette forme dépend du type de données traitées.
- **Comment encoder la base de données et le modèle ?** C'est une question de théorie de l'information : il faut une longueur de description pour le modèle et une longueur de description pour les données encodées avec lui.
- **Comment trouver le « meilleur » modèle, ou au moins un bon ?** C'est une question algorithmique : le nombre de modèles possibles est énorme et une recherche exhaustive est exclue (voir [[Recherche de la table de codes optimale]]), il faut donc une stratégie de construction.

# Exemple

Les trois familles d'algorithmes répondent aux trois questions avec les mêmes outils de fond :

- itemsets : le modèle est une [[Table de codes]], l'encodage donne à chaque entrée un code d'autant plus court que son usage est fréquent, et la recherche est menée par [[Algorithme KRIMP|KRIMP]] puis par [[Algorithme SLIM|SLIM]] ;
- séquences : le modèle est une [[Table de codes pour séquences d'événements|table de codes à quatre colonnes]], l'encodage sépare les motifs des trous entre positions couvertes, et la recherche est menée par SQS ;
- graphes : le modèle est une table de motifs de graphe, l'encodage doit distinguer les occurrences par leurs [[Ports d'un motif de graphe|ports]], et la recherche est menée par [[Compression d'un graphe par un ensemble de motifs|GraphMDL]].

# Remarque

Les trois questions ne se traitent pas indépendamment : le modèle choisi détermine ce qu'il faut encoder, l'encodage détermine le critère que l'algorithme optimise, et l'algorithme détermine ce que l'on peut effectivement atteindre. Une réponse faible à l'une des trois se répercute sur les deux autres.

Le critère commun reste la [[Taille totale d'un modèle et des données encodées|taille totale]] de la description, dont la minimisation exacte est hors de portée (voir [[Recherche de la table de codes optimale]]) ; les trois familles en donnent des approximations, résumées dans le [[Bilan de la fouille de motifs par compression|bilan de la fouille de motifs par compression]].

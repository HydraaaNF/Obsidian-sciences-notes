#dmv-pattern_mining_vs_deep_learning

# Interprétation

La rencontre entre [[Capture de motifs par l'apprentissage automatique|la capture de motifs par l'apprentissage automatique]] et les [[Réseau de neurones|réseaux de neurones]] se lit dans deux directions symétriques.

La question directe : peut-on concevoir un réseau de neurones dont les motifs appris à l'intérieur du modèle soient des [[Items, itemsets et base de transactions|itemsets]] intéressants ?

La question inverse : la fouille de motifs peut-elle servir à comprendre quels motifs un réseau profond a réellement appris ? C'est une piste de recherche encore ouverte, distincte de la précédente.

# Remarque

Le pont entre les deux domaines vient des ordres de grandeur. Les réseaux de neurones profonds traitent des millions de variables, et certaines approches acceptent des données binaires, là où chercher un [[Ensemble de motifs|ensemble de motifs]] sur des [[Données de polymorphismes nucléotidiques simples|données de polymorphismes nucléotidiques simples]] se heurte à la complexité.

La question devient alors : un réseau de neurones peut-il trouver un bon ensemble de motifs sur de telles données ?

Deux choix restent entièrement ouverts :

- l'architecture du réseau ;
- la fonction de perte à optimiser.

La suite du programme consiste à faire porter les motifs par la couche cachée d'un [[Auto-encodeur de motifs|auto-encodeur]].

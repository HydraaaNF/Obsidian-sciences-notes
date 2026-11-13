# Sommaire

## Itemsets, support et règles d'association
- [[Analyse du panier de la ménagère]]
- [[Items, itemsets et base de transactions]]
- [[Support d'un itemset]]
- [[Itemset fréquent]]
- [[Règle d'association et confiance]]
- [[Calcul des règles d'association en deux étapes]]

## Algorithme Apriori et élagage
- [[Limites de l'approche brute force]]
- [[Propriété d'anti-monotonie du support]]
- [[Treillis des itemsets]]
- [[Algorithme Apriori]]
- [[Génération des candidats par apriori-gen]]
- [[Arbre de hachage et comptage du support]]
- [[Complexité de l'algorithme Apriori]]

## Génération des règles d'association
- [[Monotonie de la confiance]]
- [[Anti-monotonie de la confiance selon la taille du conséquent]]
- [[Génération des règles d'association]]
- [[Algorithme ap-genrules]]

## Format vertical et algorithme Eclat
- [[Format vertical des transactions]]
- [[Support par intersection de tidlists]]
- [[Classes d'équivalence des itemsets]]
- [[Algorithme Eclat]]
- [[Algorithme de fouille d'une classe d'équivalence]]
- [[Recherche en profondeur d'Eclat]]

## Croissance de motifs et arbre FP
- [[Principe de la croissance de motifs FP-growth]]
- [[Arbre FP]]
- [[Construction d'un arbre FP]]
- [[Prétraitement de la base pour FP-growth]]
- [[Algorithme FP-growth]]
- [[Exemple déroulé de FP-growth]]
- [[Temps d'exécution comparés des algorithmes]]

## Itemsets maximaux et itemsets fermés
- [[Limites des itemsets fréquents]]
- [[Itemsets fréquents maximaux]]
- [[Recherche bidirectionnelle des itemsets maximaux]]
- [[Itemsets fréquents fermés]]
- [[Nombre d'itemsets par type]]
- [[Calcul des itemsets fermés]]
- [[Calcul efficace des itemsets fermés]]

## Recherche inverse et algorithme LCM
- [[Fermeture d'un itemset et extension par fermeture]]
- [[Recherche inverse des itemsets fermés]]
- [[Arbre des itemsets fermés et ordre d'exploration]]
- [[Algorithme LCM]]
- [[Réductions de la base de transactions]]

## Fouille de motifs séquentiels
### Fouille de motifs sur des données structurées
- [[Extension de la fouille de motifs aux données structurées]]
- [[Identification de motif dans des données structurées]]
- [[Chevauchement des occurrences et comptage du support]]
- [[Complexité de la fouille sur des données structurées]]
- [[Domaines d'application des motifs séquentiels]]

### Séquences et vocabulaire des motifs séquentiels
- [[Base de séquences]]
- [[Vocabulaire des motifs séquentiels]]
- [[Motif séquentiel]]
- [[Lecture informelle d'un motif séquentiel]]
- [[Familles de motifs séquentiels]]
- [[Inclusion de sous-séquence]]
- [[Support d'un motif séquentiel]]

### Énoncé du problème et panorama des algorithmes
- [[Énoncé du problème de fouille de motifs séquentiels]]
- [[Espace de recherche des motifs séquentiels]]
- [[Panorama des algorithmes de fouille de motifs séquentiels]]

### Générer et élaguer
- [[Algorithme GSP]]
- [[Génération et évaluation des candidats de GSP]]
- [[Extensions d'une séquence]]
- [[Anti-monotonie du support des motifs séquentiels]]
- [[Algorithme SPADE]]

### Croissance de motifs et bases projetées
- [[Limites des approches générer et élaguer]]
- [[Suffixe d'une séquence]]
- [[Base projetée]]
- [[Pseudo-projection]]
- [[Algorithme PrefixSpan]]

### Motifs séquentiels maximaux et clos
- [[Motif séquentiel maximal]]
- [[Motif séquentiel clos]]
- [[Algorithme CloSpan]]

### Contraintes temporelles et écart entre itemsets
- [[Contraintes temporelles en fouille de motifs séquentiels]]
- [[Durée des séquences]]
- [[Fenêtre de repliement des événements]]
- [[Contrainte d'écart temporel]]
- [[Contre-exemple à l'anti-monotonie sous contrainte d'écart maximal]]
- [[Sous-séquence contiguë]]
- [[Algorithme Gap-BIDE]]

### Fouille d'épisodes
- [[Fouille d'épisodes dans une séquence d'événements]]
- [[Séquence d'événements]]
- [[Épisode]]
- [[Fenêtre glissante de WINEPI]]
- [[Fréquence d'un épisode]]
- [[Anti-monotonie des épisodes]]
- [[Algorithme WINEPI]]
- [[Occurrence minimale d'un épisode]]
- [[Algorithme MINEPI]]

## Exercices
- [[Exercices de fouille de motifs fréquents]]
- [[Exercices de fouille de motifs séquentiels]]

# Sommaire

## Itemsets, support et règles d'association
### Itemsets et support
- [[Analyse du panier de la ménagère]]
- [[Items, itemsets et base de transactions]]
- [[Support d'un itemset]]
- [[Itemset fréquent]]
### Règles d'association et confiance
- [[Règle d'association et confiance]]
- [[Calcul des règles d'association en deux étapes]]
- [[Monotonie de la confiance]]
- [[Anti-monotonie de la confiance selon la taille du conséquent]]
- [[Génération des règles d'association]]
- [[Algorithme ap-genrules]]
### Itemsets maximaux
- [[Limites des itemsets fréquents]]
- [[Itemsets fréquents maximaux]]
- [[Recherche bidirectionnelle des itemsets maximaux]]
### Itemsets fermés et algorithme LCM
- [[Itemsets fréquents fermés]]
- [[Nombre d'itemsets par type]]
- [[Calcul des itemsets fermés]]
- [[Calcul efficace des itemsets fermés]]
- [[Fermeture d'un itemset et extension par fermeture]]
- [[Recherche inverse des itemsets fermés]]
- [[Arbre des itemsets fermés et ordre d'exploration]]
- [[Algorithme LCM]]
- [[Réductions de la base de transactions]]

## Algorithmes de fouille de motifs fréquents
### Algorithme Apriori et élagage
- [[Limites de l'approche brute force]]
- [[Propriété d'anti-monotonie du support]]
- [[Treillis des itemsets]]
- [[Algorithme Apriori]]
- [[Génération des candidats par apriori-gen]]
- [[Arbre de hachage et comptage du support]]
- [[Complexité de l'algorithme Apriori]]
### Format vertical et algorithme Eclat
- [[Format vertical des transactions]]
- [[Support par intersection de tidlists]]
- [[Classes d'équivalence des itemsets]]
- [[Algorithme Eclat]]
- [[Algorithme de fouille d'une classe d'équivalence]]
- [[Recherche en profondeur d'Eclat]]
### Croissance de motifs et arbre FP
- [[Principe de la croissance de motifs FP-growth]]
- [[Arbre FP]]
- [[Construction d'un arbre FP]]
- [[Prétraitement de la base pour FP-growth]]
- [[Algorithme FP-growth]]
- [[Exemple déroulé de FP-growth]]
- [[Temps d'exécution comparés des algorithmes]]
- [[Exercices de fouille de motifs fréquents]]

## Motifs séquentiels : énoncé et algorithmes
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
- [[Exercices de fouille de motifs séquentiels]]

## Contraintes temporelles et fouille d'épisodes
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

## Motifs de graphes : isomorphisme, support et algorithmes
### Graphes, isomorphismes et énoncé du problème
- [[Graphe]]
- [[Types de graphes]]
- [[Isomorphisme de graphes]]
- [[Isomorphisme de sous-graphe]]
- [[Fouille de motifs de graphes]]
- [[Illustration et bilan de la fouille de motifs de graphes]]
### Support d'un motif de graphe
- [[Collection de graphes et graphe unique]]
- [[Support d'un motif de graphe]]
- [[Support d'un motif dans une collection de graphes]]
- [[Anti-monotonie du support dans une collection de graphes]]
- [[Support naïf par comptage d'occurrences]]
- [[Support par chevauchement]]
- [[Support par image minimale]]
### Algorithmes de fouille de motifs de graphes
- [[Algorithmes par fusion de motifs]]
- [[Algorithme FSG]]
- [[Croissance de motifs de graphes]]
- [[Panorama des algorithmes de croissance de motifs de graphes]]
### Codes canoniques et élagage
- [[Code canonique d'un graphe]]
- [[Code DFS d'un graphe]]
- [[Ordre et code DFS minimal]]
- [[Élagage par codes canoniques]]

## Fouille de sous-groupes
### Motifs et mesures de qualité
- [[Principe de la découverte de sous-groupes]]
- [[Tâche de découverte de sous-groupes]]
- [[Motif de sous-groupe]]
- [[Sélecteur d'un motif de sous-groupe]]
- [[Fonction de qualité d'un sous-groupe]]
- [[Matrice de confusion d'un sous-groupe]]
- [[Exactitude relative pondérée]]
- [[Fonction de qualité pour cible numérique]]
### Attributs cibles et modèles exceptionnels
- [[Attributs de description et attributs cibles]]
- [[Découverte de modèles exceptionnels]]
- [[Classe de modèle et modèle exceptionnel]]
### Recherche exhaustive et heuristique
- [[Recherche des sous-groupes]]
- [[Espace de recherche des sous-groupes]]
- [[Estimation optimiste d'une fonction de qualité]]
- [[Élagage top-k]]
### Redondance et diversité
- [[Limites du classement top-k]]
- [[Sélection d'un ensemble de sous-groupes]]
- [[Recherche en faisceau diversifiée]]
- [[Degrés de diversité d'un ensemble de sous-groupes]]

## Fondements et encodage de la visualisation
### Place de la visualisation dans l'analyse de données
- [[Cadre d'analyse de la visualisation]]
- [[Processus d'extraction de connaissances dans les bases de données]]
- [[Visualisation assistée par ordinateur]]
- [[Complémentarité de la visualisation et des méthodes automatiques]]
- [[Visualisation scientifique et visualisation d'information]]

### Système de visualisation et boucles d'interaction
- [[Boucle du système de visualisation]]
- [[Faire entrer l'ordinateur dans la boucle d'analyse]]
- [[Analyse pilotée par l'utilisateur]]
- [[Représentation externe et déchargement cognitif]]
- [[Interactivité de la visualisation]]

### Perception et attention
- [[Perception visuelle et traitement préconscient]]
- [[Limites de la perception humaine]]
- [[Cécité au changement]]

### Types de données et représentations visuelles
- [[Types de jeux de données]]
- [[Attribut et types d'attributs]]
- [[Diagramme en barres et diagramme en lignes]]
- [[Nuage de points pour données multidimensionnelles]]
- [[Quartet d'Anscombe]]
- [[Lecture d'une boîte à moustaches]]
- [[Représentation visuelle des réseaux]]
- [[Graphique de flux]]
- [[Visualisation de tenseurs]]

### Abstraction des tâches d'analyse
- [[Abstraction des tâches d'analyse]]
- [[Actions d'une tâche d'analyse]]
- [[Recherche et requête dans une visualisation]]
- [[Cibles d'une tâche d'analyse]]
- [[Questions du comment en conception de visualisation]]
### Principes de composition de la vue
- [[Exprimer toutes les données dans la vue]]
- [[Séparer les marques sans recouvrement]]
- [[Ordonner et aligner les marques]]

### Canaux visuels, couleur et techniques d'encodage
- [[Coordonnées parallèles]]
- [[Loi de puissance de Stevens]]
- [[Canaux visuels et efficacité d'encodage]]
- [[Erreurs de discrimination des encodages visuels]]
- [[Encodage par la couleur]]
- [[Palettes de couleurs de ColorBrewer]]
- [[Analyse spatio-temporelle par partition progressive]]

## Interaction, validation et analytique immersive
### Manipulation et vues multiples
- [[Diagramme en ensembles parallèles]]
- [[Manipulation d'une visualisation]]
- [[Vues multiples coordonnées]]
- [[Réduction des données affichées]]
### Validation de la conception
- [[Validation d'une visualisation]]
- [[Échecs d'une visualisation]]
- [[Bonnes pratiques de conception d'une visualisation]]
- [[Cycle de vie de la conception d'une visualisation]]
### Analytique immersive
- [[Analytique immersive]]
- [[Cube espace-temps pour l'exploration de trajectoires]]
- [[GeoGate, cube espace-temps en réalité augmentée]]
- [[Bento Box, vues multiples de simulations en réalité virtuelle]]
- [[FiberClay, sculpture de trajectoires en trois dimensions]]
- [[Outils de construction pour l'analytique immersive]]
- [[Défis de recherche de l'analytique immersive]]

## Apprentissage profond pour la fouille de motifs
### Du problème de l'ensemble de motifs aux réseaux de neurones
- [[Capture de motifs par l'apprentissage automatique]]
- [[Ensemble de motifs]]
- [[Complexité de la recherche d'un ensemble de motifs]]
- [[Données de polymorphismes nucléotidiques simples]]
- [[Fouille de motifs et réseaux de neurones profonds]]

### Architecture de l'auto-encodeur de motifs
- [[Auto-encodeur de motifs]]
- [[Couche de motifs]]
- [[Poids binaires et optimisation différentiable]]

### Encodage et décodage de la couche de motifs
- [[Encodage d'une transaction en motifs]]
- [[Décodage d'une couche de motifs]]
- [[Fonction de bornage dans un intervalle]]

### Entraînement de l'auto-encodeur de motifs
- [[Boucle d'apprentissage de l'auto-encodeur de motifs]]
- [[Perte de reconstruction pondérée par la parcimonie]]
- [[Exemple déroulé d'apprentissage de motifs par auto-encodeur]]

### Résultats, passage à l'échelle et prolongements
- [[Qualité des motifs selon le nombre de variables]]
- [[Temps de calcul selon le nombre de variables]]
- [[Passage à l'échelle de l'apprentissage de motifs]]
- [[Prolongement vers d'autres langages de motifs]]
- [[Questions ouvertes de la fouille de motifs par descente de gradient]]

## De l'explosion des motifs à la description minimale
### Limites de la fouille exhaustive des motifs
- [[Efficacité et utilité de la fouille de motifs]]
- [[Familles d'approches pour maîtriser le nombre de motifs]]
- [[Énoncé standard de la fouille de motifs]]
- [[Explosion du nombre de motifs]]
- [[Écart entre les motifs demandés et les motifs utiles]]
- [[Motif comme propriété locale des données]]
- [[Factorisation des données en modèle et en données couvertes]]

### Principe de description minimale et complexité de Kolmogorov
- [[Principe de la longueur minimale de description]]
- [[Compromis entre longueur du modèle et longueur des données]]
- [[Complexité de Kolmogorov]]

### Tables de codes et mesure de longueur
- [[Panorama des approches par compression en fouille de motifs]]
- [[Table de codes]]
- [[Couverture d'une transaction par une table de codes]]
- [[Table de codes standard]]
- [[Probabilité et longueur optimale d'un code]]
- [[Longueur de description d'une table de codes]]
- [[Longueur de description d'une base encodée]]
- [[Taille totale d'un modèle et des données encodées]]
- [[Recherche de la table de codes optimale]]

## Algorithmes de compression et bilan
### Tables de codes pour les itemsets
- [[Algorithme KRIMP]]
- [[Élagage après acceptation d'une table de codes]]
- [[Propriétés des tables de codes de KRIMP]]
- [[Applications des tables de codes]]
- [[Classification par compression avec des tables de codes]]
- [[Algorithme SLIM]]

### Tables de codes pour les séquences
- [[Table de codes pour séquences d'événements]]
- [[Longueur des codes de motifs et de trous]]
- [[Longueur de description d'une base de séquences]]
- [[Longueur de description d'une table de codes de séquences]]
- [[Algorithme de sélection de candidats de SQS]]
- [[Algorithme de recherche progressive de SQS]]

### Tables de codes pour les graphes et bilan
- [[Compression d'un graphe par un ensemble de motifs]]
- [[Table de codes de motifs de graphes]]
- [[Perte d'information d'une table de codes sans ports]]
- [[Ports d'un motif de graphe]]
- [[Réduction du nombre de motifs de graphes par compression]]
- [[Version progressive de GraphMDL]]
- [[Bilan de la fouille de motifs par compression]]
- [[Trois questions de conception d'une approche par compression]]

## Explicabilité en apprentissage supervisé : cadrage et formes
### Cadrage sur l'intelligence artificielle et l'explicabilité
- [[Intelligence]]
- [[Place de l'apprentissage automatique parmi les disciplines]]
- [[Apprentissage à partir de données étiquetées]]
- [[Interprétabilité]]
- [[Explicabilité]]
- [[Taxonomie des techniques d'explicabilité]]
### Formes et motivations de l'explication
- [[Explication]]
- [[Formes d'explication selon la modalité des données]]
- [[Motivations de l'explicabilité]]
- [[Affaires révélant les risques des modèles opaques]]
- [[Cadre légal et éthique de l'explicabilité]]

## Modèles interprétables et explications par conception
### Modèles interprétables
- [[Modèle linéaire]]
- [[Lien logistique comme modèle interprétable]]
- [[Arbre de décision]]
- [[Règles, listes et ensembles de décision]]
- [[Méthodes à base d'exemplaires]]
- [[Neurone formel]]
- [[Architectures et représentations des réseaux]]
- [[Méthodes d'ensemble et machines à vecteurs de support]]
### Explications par conception
- [[Familles d'analyses internes d'un modèle]]
- [[Explications par concepts et prototypes]]
- [[Réseaux de neurones contrefactuels]]
- [[Shapelets]]

## Explications après coup, contrefactuels et évaluation
### Explications globales
- [[Explication globale]]
- [[Graphique de dépendance partielle]]
- [[Importance des variables par agrégation]]
- [[Substituts globaux par arbre et par règles]]
- [[Contrefactuels globaux]]
### Explications locales
- [[Explication locale]]
- [[Représentation interprétable]]
- [[LIME]]
- [[Méthodes d'attribution par gradients]]
- [[Valeur de Shapley]]
- [[SHAP]]
- [[Règles locales d'explication]]
### Explications contrefactuelles
- [[Explication contrefactuelle]]
- [[Apprentissage de contrefactuels]]
- [[Algorithmes de génération de contrefactuels]]
- [[Contrefactuels pour le texte]]
### Évaluation et questions ouvertes
- [[Critères et métriques d'évaluation d'une explication]]
- [[Évaluation de la compréhension et de la confiance]]
- [[Protocole de comparaison d'explications]]
- [[Questions ouvertes de l'explicabilité]]

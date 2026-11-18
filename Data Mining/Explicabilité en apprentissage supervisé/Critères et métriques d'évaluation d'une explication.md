#dmv-xai

# Définition

Évaluer une explication la confronte à deux familles de critères.

- les critères **fonctionnels** portent sur l'explication produite et sur la méthode qui la produit
- les critères **centrés utilisateur** portent sur la personne qui reçoit l'explication

# Propriétés

Les critères fonctionnels se répartissent en trois familles.

- la **complexité**
- la **(non-)fidélité**, dont l'**adhérence** est une composante
- la **stabilité et la robustesse**

Les critères centrés utilisateur se répartissent en deux familles.

- la **compréhension**, déclinée en **compréhensibilité** et en **plausibilité**
- la **confiance**, déclinée en **confiance**, **défiance** et **complaisance**

Les métriques fonctionnelles se rattachent à l'un des deux objets mesurés, l'explication ou la méthode.

| Objet mesuré | Critère | Métrique |
| --- | --- | --- |
| Explication | adhérence | métriques de classification et de régression |
| Explication | complexité | dépend du type d'explication |
| Explication | fidélité | techniques d'occlusion, réduction d'accuracy |
| Méthode | stabilité et robustesse | coefficient de Jaccard, stability index, métriques de rang |
| Méthode | sans intitulé de critère | temps d'exécution, empreinte mémoire |

Une explication est donc jugée sur plusieurs axes à la fois : sa taille, son accord avec le modèle, la reproductibilité de la méthode qui la produit, le temps d'exécution et la mémoire que coûte son calcul.

# Interprétation

La frontière entre les deux familles ne sépare pas des types d'explications, mais des objets de mesure. Une grandeur fonctionnelle se calcule sur l'explication seule ou sur la méthode seule, sans intervention humaine ; une grandeur centrée utilisateur se mesure sur la personne qui reçoit l'explication.

La fidélité est le critère, l'adhérence en est la composante mesurable. Une explication fidèle rend compte de ce que le modèle calcule réellement, et l'adhérence rapporte l'explication au comportement du modèle au moyen de métriques de classification ou de régression. L'évaluation de la fidélité repose en pratique sur des techniques d'occlusion, qui font varier une partie de l'entrée pour observer la réaction de l'explication, et sur la réduction d'accuracy qui en résulte.

La mesure de la complexité dépend du type d'explication produite : à défaut d'unité commune, elle tient lieu d'exigence de compacité.

La stabilité et la robustesse sont des propriétés de la méthode plutôt que de l'explication isolée : elles se mesurent par le coefficient de Jaccard, le stability index et des métriques de rang, auxquels s'ajoutent le temps d'exécution et l'empreinte mémoire.

Les critères centrés utilisateur ne se calculent pas : compréhension et confiance s'établissent au moyen de tâches substitutives et de questionnaires, détaillés dans l'[[Évaluation de la compréhension et de la confiance]] et mis en œuvre dans le [[Protocole de comparaison d'explications]].

# Exemple

La confiance d'un utilisateur se relève par un questionnaire ; les réponses d'exemple de l'utilisateur J sont notées sur sept, alors que le questionnaire lui-même se gradue de 1 à 6.

| Question | Réponse de l'utilisateur J |
| --- | --- |
| Quelle confiance avez-vous dans l'outil ? Éprouvez-vous un sentiment de confiance envers lui ? | 5/7 |
| Les actions de l'outil sont-elles prévisibles ? | 6/7 |
| L'outil est-il fiable ? | 3/7 |
| L'outil est-il efficace dans ce qu'il fait ? | 4/7 |
| Moyenne | 4.5/7 |

Les quatre questions portent sur la confiance et reçoivent chacune une note.

# Remarque

Trois questions restent ouvertes pour une explication : que révéler, quelle interactivité offrir, quelle représentation adopter. Les formes produites sont en effet hétérogènes, et un même jeu de critères doit les comparer.

- l'attribution locale des variables d'une prédiction tabulaire, du ressort d'une [[Explication locale]]
- la mise en évidence des mots d'une phrase pour un modèle de texte, par exemple avec [[LIME]] ou des ancres
- le contrefactuel d'une image
- les cartes de saillance d'une grille de méthodes

Les approches d'explicabilité sont rarement évaluées sur des utilisateurs : l'essentiel des mesures reste fonctionnel, alors que la compréhension et la confiance exigent une étude conduite avec des personnes.

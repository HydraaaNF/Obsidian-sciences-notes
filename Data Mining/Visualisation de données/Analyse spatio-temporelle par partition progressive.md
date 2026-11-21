#dmv-visualization

# Définition

L'**analyse spatio-temporelle par partition progressive** découpe itérativement un jeu de données spatio-temporel en sous-ensembles et extrait, à chaque niveau de découpage, des motifs multidimensionnels : la partition successive ramène chaque étape à un volume traité plus faible, sans perdre la possibilité de descendre jusqu'au détail.

# Propriétés

L'encodage des motifs extraits repose sur un glyphe de type boîte à moustaches simplifié :

- une échelle de déviation graduée de $-100\%$ à $0$ puis à $+100\%$ ;
- les quartiles $Q_1$, $Q_2$ (la médiane) et $Q_3$ repérés sur cette échelle ;
- une surface dont la hauteur représente le trafic cumulé et la largeur le trafic d'une heure ;
- une couleur qui code la valeur absolue de la déviation, du bleu pour les valeurs faibles au rouge pour les valeurs fortes.

Le glyphe admet trois formes : un rectangle vertical, une boîte inclinée et un anneau où les quartiles deviennent des arcs.

# Exemple

Une interface d'exploration de données de trafic réunit quatre panneaux coordonnés :

- un panneau de partition, où les dimensions (produit, région, mois) se déploient en flux successifs, la déviation par rapport à une valeur de référence étant encodée par une échelle de couleur allant du bleu au rouge ;
- un panneau de barres horizontales, une barre par catégorie de produit ;
- un panneau de séries temporelles, plusieurs courbes sur les dates de 2014 et 2015, avec des points de repère marqués ;
- une carte où chaque région est figurée par des cercles concentriques.

L'encodage suit une progression en quatre niveaux, appliquée à quatre types de données :

| Type de données | Basic chart | Enable comparison | Encode deviation | Encode partition |
| :--- | :--- | :--- | :--- | :--- |
| Temporel catégoriel numérique | barres horizontales, une mesure par catégorie | barres horizontales alignées, comparaison entre groupes | barres avec bornes de déviation | barres horizontales empilées par catégorie |
| Temporel | une série de courbes | plusieurs courbes superposées | courbe avec bande de déviation ombrée | série découpée par intervalles |
| Spatial | carte à régions circulaires | carte comparant deux couleurs de régions | carte à régions avec bornes de déviation | carte à territoires partitionnés |
| Origine-destination | carte de trajectoire | trajectoires comparées | non illustré | flux partitionnés avec direction |

# Interprétation

Les quatre colonnes du tableau forment une progression : le graphique de base montre la valeur, la comparaison ajoute une seconde série, l'encodage de la déviation rapporte la valeur à une référence, et l'encodage de la partition découpe la valeur selon les catégories.

Le choix de l'encodage dépend du type de données : les séries temporelles passent de la courbe unique à la courbe découpée, les données spatiales de la région colorée à la carte partitionnée, et le croisement origine-destination avec l'encodage de la déviation reste sans illustration.

# Remarque

Le jeu de données est de type spatio-temporel, avec des attributs catégoriels, quantitatifs et des liens origine-destination : voir [[Types de jeux de données]].

Les panneaux sont liés entre eux, ce qui permet de sélectionner une zone sur la carte et de lire ses profils dans les autres vues : voir [[Vues multiples coordonnées]] et [[Exprimer toutes les données dans la vue]].

#ml-1

# Définition

Les **hyper-paramètres** sont tous les réglages qu'un entraînement ne détermine pas lui-même et qui restent à la charge de la personne qui conçoit le modèle :

- le nombre et la taille des couches, les fonctions d'activation ;
- la fonction de perte, l'[[Optimiseurs|algorithme d'optimisation]], le taux d'apprentissage ;
- le nombre d'époques, la taille de lot, etc.

Ils se distinguent des paramètres, dont les valeurs sont trouvées par l'apprentissage.

# Algorithme

La méthode consiste à **essayer et à comparer** les valeurs candidates, en mesurant sur le **jeu de développement** :

- entraîner le modèle pour chacune des combinaisons d'hyper-paramètres envisagées ;
- comparer les performances obtenues sur le jeu de développement ;
- retenir la combinaison qui y donne la meilleure performance.

Le jeu de test n'intervient jamais dans ce choix : il ne sert qu'à rapporter la performance finale. Voir [[Jeux d'entraînement, de développement et de test]] et [[Méthode de validation]].

# Remarque

L'entraînement lui-même peut échouer, indépendamment du choix de la perte :

- en régression logistique, la perte est convexe et admet un seul minimum : l'optimisation l'atteint ;
- dans un [[Perceptron multicouche|perceptron multicouche]] (MLP), la perte n'est pas convexe : le résultat dépend de l'initialisation aléatoire ;
- sur la démonstration du [[Problème du ou exclusif|XOR]], avec 2 neurones cachés environ une graine sur deux donne un réseau qui fonctionne, alors qu'avec 8 neurones les 20 graines essayées fonctionnent.

Un réseau plus large est donc souvent plus facile à entraîner.

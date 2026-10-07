# Définition

Un **processus stochastique** est une collection de variables aléatoires indexées par le temps :

$$X = \{X_1, \ldots, X_T\}$$

Un **champ aléatoire** est une collection de variables aléatoires indexées sur une grille :

$$X = \{X_s \mid s \in S\}$$

# Interprétation

Les données réelles présentent souvent une structure temporelle (des mesures évoluant au cours du temps) ou spatiale (des valeurs disposées sur une grille), que les modèles doivent prendre en compte pour exploiter l'information structurelle.

- Un processus stochastique modélise l'**évolution temporelle** : il est le cadre des [[Chaîne de Markov à temps discret|modèles de Markov]] et des [[Modèle de Markov caché|modèles de Markov cachés]], des [[Processus de naissance et de mort|processus de naissance et de mort]], des [[Processus de Poisson|processus de Poisson]] et des [[File d'attente|systèmes de files d'attente]].
- Un champ aléatoire modélise les **interactions spatiales** : il est le cadre des [[Champ aléatoire de Markov|champs aléatoires de Markov]].

# Remarque

Une relation temporelle est une forme de relation spatiale.

Voir [[Espaces d'états et d'indices d'un processus]] pour l'ensemble d'indices et l'espace d'états, [[Fonctions de répartition d'un processus stochastique]] pour les fonctions de répartition, et [[Processus indépendant et stationnaire]] pour l'indépendance et la stationnarité.

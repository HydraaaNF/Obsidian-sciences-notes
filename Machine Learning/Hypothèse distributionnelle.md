#ml-1

# Définition

**Hypothèse distributionnelle** : deux mots qui apparaissent dans les mêmes contextes ont des sens proches, donc doivent recevoir des vecteurs proches.

« You shall know a word by the company it keeps » : le sens d'un mot se lit dans les mots qui l'entourent.

Elle fixe l'objectif d'une représentation des mots : un vecteur par mot, dont la proximité reproduit la proximité de sens.

# Interprétation

Un encodage [[Encodage des valeurs symboliques|one-hot]] traite chaque mot comme un symbole isolé : deux codes distincts sont à la même distance, quelle que soit la parenté des mots.

$$
\|\text{cat} - \text{dog}\| = \|\text{cat} - \text{bird}\| = \|\text{cat} - \text{carburettor}\| = \sqrt{2}
$$

Rien dans ces codes ne rapproche « cat » de « dog » plutôt que de « carburettor ». L'hypothèse distributionnelle propose de remplacer ces codes par des vecteurs dont la géométrie porte le sens : des vecteurs proches pour des sens proches.

# Exemple

« The ___ is sleeping on the sofa » : « cat » et « dog » remplissent le trou, « bird » rarement, « carburettor » jamais.

Les mots qui remplissent le même trou apparaissent dans les mêmes contextes : l'hypothèse distributionnelle leur associe des vecteurs proches.

Apprendre ces vecteurs ne demande aucune étiquette : il suffit de prédire le contexte d'un mot, et n'importe quel texte fournit les exemples.

# Remarque

Deux familles de méthodes exploitent l'hypothèse :

- compter les cooccurrences mot-contexte sur un grand corpus, puis compresser la matrice obtenue (analyse sémantique latente) ;
- prédire le contexte, ce que fait [[word2vec]].

Dans les deux cas, les vecteurs obtenus pour les mots sont des [[Plongement|plongements]], matérialisés par la [[Couche de plongement]] comme des lignes de matrice apprises.

Une représentation plus fine associe un vecteur à chaque occurrence d'un mot, selon la phrase où il apparaît, au lieu d'un seul vecteur par mot.

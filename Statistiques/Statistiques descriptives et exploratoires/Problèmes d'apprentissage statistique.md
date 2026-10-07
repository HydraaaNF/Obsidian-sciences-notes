# Définition

Soit $Z_1, Z_2, \dots, Z_n$ un [[Échantillon et échantillonnage|échantillon aléatoire]] de taille $n$ d'une distribution inconnue de densité $p(z)$ ; les variables $Z_i$ sont indépendantes et identiquement distribuées (iid).

L'[[Modélisation statistique et apprentissage automatique|apprentissage statistique]] considère trois problèmes :

1. **Classification** : $Z = (X, Y) \in \mathbb{R}^d \times \{-1, 1\}$ ; étant donné un nouveau $x$, estimer $\mathbb{P}(Y \mid X = x)$.
2. **Régression** : $Z = (X, Y) \in \mathbb{R}^d \times \mathbb{R}$ ; étant donné un nouveau $x$, estimer $\mathbb{E}[Y \mid X = x]$.
3. **Estimation de densité** : $Z \in \mathbb{R}^d$ ; étant donné un nouveau $z$, estimer $p(z)$.

# Remarque

Voir aussi l'[[Espace d'hypothèses]], la [[Fonction de perte]] et, pour la classification, la [[Règle de décision de Bayes]].

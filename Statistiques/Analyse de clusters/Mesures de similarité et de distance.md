# Définition

La similarité entre deux objets appelle une **notion de distance** : toute mesure de similarité $d(x_i, x_j)$ entre deux objets peut être utilisée pour résoudre le problème de [[Clustering|clustering]]. La mesure adéquate dépend fortement de la nature des données et de la nature du problème.

Trois familles de mesures se distinguent :

- **les mesures de distance** : distance euclidienne, distance de Manhattan, distance de Mahalanobis, distance du $\chi^2$, etc. ;
- **les similarités** (sans inégalité triangulaire) : similarité cosinus, appariement de gabarits (template matching), distance d'édition (edit distance), vraisemblance généralisée (generalized likelihood), etc. ;
- **les mesures conceptuelles** : tout ce que l'on peut imaginer.

# Remarque

Ces mesures sont l'ingrédient de base des algorithmes de clustering : le partitionnement par [[k-means]] comme le [[Clustering hiérarchique|clustering hiérarchique]] reposent sur les proximités entre objets. La même idée de comparaison deux à deux se retrouve pour les variables d'un jeu de données, avec la [[Matrice de corrélation]]. Hors du clustering, la notion de distance sert aussi à mesurer la précision d'un estimateur, via la [[Distance en moyenne d'ordre p|distance en moyenne d'ordre p]].

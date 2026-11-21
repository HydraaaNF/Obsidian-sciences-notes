#ml-2

# Interprétation

Une couche dense du [[Perceptron multicouche]] connecte chaque neurone à toute l'image : chaque neurone possède un poids par pixel et par canal, et aucun poids n'est partagé entre deux positions. Sur une image de taille réaliste, le nombre de paramètres à apprendre devient considérable, et un motif appris en un endroit de l'image n'est pas reconnu ailleurs sans réapprentissage.

La [[Couche de convolution]] répond à ces deux limites en faisant glisser un petit noyau sur l'image :

- les motifs détectés sont **locaux** : contours, textures, petits arrangements de pixels ;
- ce sont les **mêmes poids** à toutes les positions (*weight sharing*) ;
- un motif est détecté partout où il apparaît (équivariance par translation).

Le noyau est donc un détecteur de motif réutilisé sur toute l'image, au lieu d'un jeu de poids propre à chaque position.

# Exemple

Couche dense de 1000 neurones sur une image $224 \times 224$ en RGB :

$$224 \times 224 \times 3 \times 1000 \approx 150 \text{ millions}$$

de poids appris, hors biais, et chaque neurone regarde l'image entière.

Convolution par 5 noyaux de taille $3 \times 3 \times 3$ :

$$5 \times 3 \times 3 \times 3 = 135$$

poids appris, hors biais, soit plus d'un million de fois moins.

| | Couche dense de 1000 neurones | Convolution à 5 noyaux |
| --- | --- | --- |
| Poids appris (hors biais) | $224 \times 224 \times 3 \times 1000 \approx 150$ millions | $5 \times 3 \times 3 \times 3 = 135$ |
| Portée d'une unité | l'image entière | une fenêtre $3 \times 3$ |
| Partage des poids | aucun | noyau identique à chaque position |

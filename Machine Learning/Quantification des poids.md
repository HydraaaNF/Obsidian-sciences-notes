#ml-3

# Définition

La **quantification des poids** consiste à stocker les poids d'un modèle sur moins de bits que la précision usuelle, par exemple 8 bits, 4 bits, voire moins. Elle réduit la [[Taille de stockage des poids]] d'un modèle sans modifier son architecture.

# Propriétés

- Le passage de 16 à 4 bits rend le modèle quatre fois plus petit, pour une petite perte de qualité.
- Un modèle quantifié tient sur un seul GPU.
- Les petits modèles quantifiés tiennent sur un portable.
- Pour $10^{12}$ poids, la taille passe de 2 To en 16 bits à 1 To en int8 et 0,5 To en int4.

# Remarque

La précision usuelle des grands modèles de langage actuels est de 16 bits. Les réseaux classiques utilisent 32 bits, et 64 bits n'est jamais utilisé. La quantification est une étape de compression d'un [[Cycle de vie d'un grand modèle de langage]].

#ml-3

# Définition

Un modèle de $10^{12}$ poids, soit 1000 milliards de paramètres, peut représenter « l'ensemble » du savoir de l'humanité : il simule le raisonnement, il génère du texte, du code, des images et de l'audio, et il interprète ces mêmes modalités. La taille de stockage de ses poids est le nombre d'octets qu'ils occupent une fois écrits.

# Propriétés

La taille se calcule à partir du nombre de poids et du nombre de bits retenu pour chacun :

$$\text{taille} = \text{poids} \times \text{bits} / 8 \text{ (octets)}$$

Le résultat croît linéairement avec le nombre de poids et avec la précision de leur format. Chaque élément d'un [[Tenseur|tenseur]] de poids coûte le nombre de bits de son format, et la division par 8 convertit les bits en octets.

# Exemple

Pour $10^{12}$ poids, la taille de stockage varie d'un facteur 16 selon la précision :

| Précision | Bits | Taille (téraoctets) |
|---|---:|---:|
| float64 | 64 | 8 |
| float32 | 32 | 4 |
| bfloat16 | 16 | 2 |
| int8 | 8 | 1 |
| int4 | 4 | 0,5 |

16 bits est la précision usuelle des LLM actuels ; 32 bits est celle des réseaux classiques, et 64 bits n'est jamais utilisé.

# Remarque

La [[Quantification des poids]] consiste à stocker les poids sur moins de bits (8, 4, voire moins) : passer de 16 à 4 bits réduit la taille d'un facteur 4, pour une faible perte de qualité, et permet l'exécution sur un seul GPU, ou sur un ordinateur portable pour les petits modèles.

La taille obtenue fixe l'ordre de grandeur du matériel d'hébergement du modèle, question traitée dans le [[Cycle de vie d'un grand modèle de langage]].

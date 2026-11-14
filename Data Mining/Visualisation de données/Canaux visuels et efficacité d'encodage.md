#dmv-visualization

# Définition

Un **canal visuel** est une dimension perceptive sur laquelle une valeur peut être encodée. Le système visuel humain discrimine les stimuli selon deux dimensions majeures : la couleur et la forme.

Encoder les données consiste à affecter chaque attribut au canal qui en rend la lecture la plus fidèle.

# Propriétés

L'efficacité des canaux décroît du haut vers le bas d'une échelle qui va de $+$ à $-$.

| Canal | Exemple |
| :--- | :--- |
| Longueur (taille 1D) | segments de longueurs croissantes |
| Luminance de la couleur | dégradé de gris |
| Saturation de la couleur | teintes de gris puis de couleur |
| Position sur une échelle commune | points repérés sur un même axe |
| Position sur une échelle non alignée | points repérés sur des axes distincts |
| Inclinaison et angle | segments d'orientation variable |
| Volume (taille 3D) | solides de tailles croissantes |
| Aire (taille 2D) | surfaces de tailles croissantes |
| Courbure | arcs de courbure croissante |
| Profondeur (position 3D) | points situés à des profondeurs différentes |

# Interprétation

L'encodage visuel est donc un problème d'affectation : à chaque attribut correspond un canal, et le classement fournit l'ordre de préférence lorsque plusieurs canaux sont disponibles pour le même attribut.

La position sur une échelle commune et la position sur une échelle non alignée occupent deux rangs distincts du classement : deux vues qui placent les mêmes valeurs sur un axe partagé ou sur des axes séparés ne se lisent pas avec la même précision.

# Remarque

La couleur n'est pas un canal unique : elle se décompose en teinte, saturation et luminance, chacune avec sa propre sensibilité de l'œil, ce que détaille [[Encodage par la couleur]].

Les erreurs de discrimination mesurées pour neuf encodages élémentaires sont décrites dans [[Erreurs de discrimination des encodages visuels]].

La loi de puissance de Stevens, $S = I^N$, relie la sensation perçue à l'intensité du stimulus et fonde la lecture quantitative des canaux : voir [[Loi de puissance de Stevens]].

Le traitement parallèle et préconscient d'une partie de l'information visuelle, qui explique la hiérarchie entre canaux, est décrit dans [[Perception visuelle et traitement préconscient]].

Le choix du canal pour chaque type de donnée est illustré par les quatre niveaux d'encodage décrits dans [[Analyse spatio-temporelle par partition progressive]].

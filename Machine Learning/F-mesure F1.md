#ml-1

# Définition

La F-mesure $F_1$ résume la [[Précision et rappel|précision et le rappel]] en une seule valeur : c'est leur moyenne harmonique.

$$F_1 = 2 \times \frac{\text{Prec} \times \text{Rec}}{\text{Prec} + \text{Rec}}$$

Elle vaut $0$ pour un modèle mauvais et $1$ pour un modèle parfait.

# Interprétation

- La moyenne est harmonique et non arithmétique, de sorte qu'un modèle doit être bon à la fois en précision et en rappel : une seule des deux mesures faible suffit à faire chuter $F_1$.
- Cette propriété rend $F_1$ utile en recherche d'information, où l'on veut retrouver tous les documents pertinents sans ramener de documents hors sujet.
- Un modèle parfait retourne tous les documents de la classe $C$ (rappel de $1$) et seulement ceux-là (précision de $1$), donc $F_1 = 1$.

# Remarque

- Sur un graphique précision-rappel, deux modèles se comparent mal lorsque l'un privilégie la précision (point A, en haut à gauche) et l'autre le rappel (point B, en bas à droite) : la F-mesure tranche en combinant les deux dimensions.
- Comme la précision et le rappel, $F_1$ est défini par classe ; l'agrégation des scores sur plusieurs classes est traitée dans [[Moyennes macro et micro]].

#ml-1

# Définition

Trois familles de tâches se distinguent par la nature de la valeur prédite :

- la **régression** prédit des valeurs numériques ;
- la **classification** prédit des valeurs symboliques ;
- le **clustering** s'apparente à une classification non supervisée.

# Exemple

Les tâches d'apprentissage se distinguent par la forme de leur entrée et de leur sortie.

| Tâche | Formalisation |
|---|---|
| Savoir si une position d'échecs est meilleure qu'une autre | $\text{État} \times \text{État} \to [-1, 1]$ |
| Prédire le prix d'une maison | $\text{Description} \to \mathbb{R}^+$ |
| Détecter si une séquence de commandes peut être une attaque | $\text{Liste}(\text{Commandes}) \to [0, 1]$ |
| Détecter si une arme est présente sur une image | $\text{Liste}(\text{Image}) \to [0, 1]$ |
| Distinguer une voiture d'un camion sur une image | $\text{Image} \to \{\text{Voiture}, \text{Camion}, \text{Autre}\}$ ou $\text{Image} \to \{[0, 1], [0, 1], [0, 1]\}$ |
| Détecter si une arme est présente sur une vidéo | $\text{Liste}(\text{Image}) \to [0, 1]$ |
| Savoir si deux mots sont synonymes | $\text{Mot} \times \text{Mot} \to [0, 1]$ |
| Savoir si deux textes disent la même chose | $\text{Liste}(\text{Mot}) \times \text{Liste}(\text{Mot}) \to [0, 1]$ |
| Changer le visage de quelqu'un sur une image | $\text{Image} \times \text{Image} \times \text{Image} \to \text{Image}$ |
| Donner les thèmes d'un texte | $\text{Texte} \to ??$ |
| Donner le genre musical d'une chanson | $\text{Trames audio} + \text{métadonnées} \to ??$ |

La forme de la sortie fixe la nature de la tâche, non l'intervalle dans lequel elle prend ses valeurs :

- une sortie **numérique** relève de la régression : le prix d'une maison dans $\mathbb{R}^+$, le score d'une position d'échecs dans $[-1, 1]$ ;
- une sortie **symbolique** relève de la classification : une espèce, un ensemble de classes comme $\{\text{Voiture}, \text{Camion}, \text{Autre}\}$ ;
- les tâches de détection ont pour sortie un score dans $[0, 1]$, qui se lit comme l'appartenance à une classe et non comme une grandeur à prédire ;
- une sortie elle-même complexe (une image) demande un modèle qui produit un objet structuré ;
- les deux dernières tâches restent à formaliser, la forme de leur sortie n'étant pas fixée.

# Exemple

Les mêmes mesures, la taille et le niveau de gris d'un oiseau, servent à illustrer les deux tâches.

En **régression**, la variable prédite est le niveau de gris de l'oiseau, une grandeur numérique : les points du nuage sont approchés par une courbe.

En **classification**, la variable prédite est l'espèce, une étiquette symbolique : la frontière de décision est horizontale, à un niveau de gris constant, et range les cormorans, plus sombres, au-dessus des cygnes, plus clairs. Les deux espèces se recouvrent en taille : la taille seule ne suffit pas à les distinguer, et l'entrée de la classification est le couple (taille, niveau de gris).

# Remarque

La régression et la classification sont les deux tâches **supervisées** : chaque exemple d'apprentissage est accompagné de la valeur à prédire, voir [[Apprentissage supervisé]].

Le clustering est leur contrepartie **non supervisée** : les groupes sont constitués à partir des seules observations, sans étiquette fournie, voir [[Apprentissage non supervisé]].

La [[Régression linéaire]] est un cas particulier de régression, où la courbe ajustée est une droite.

La régression et la classification comptent parmi les [[Problèmes d'apprentissage statistique]].

#ml-1

# Définition

La couche de sortie d'un classifieur à $K$ classes s'écrit

$$z = hA^\top + b$$

où $h$ est la représentation produite par les couches qui précèdent, $A$ la matrice des poids et $b$ le biais. La ligne $c$ de $A$ est un vecteur $a_c$, un par classe, et le score de la classe $c$ vaut

$$z_c = h \cdot a_c + b_c$$

# Interprétation

Le score d'une classe mesure l'accord entre la représentation $h$ et le vecteur de cette classe. Un produit scalaire est grand lorsque les deux vecteurs pointent dans le même sens.

Pour obtenir un score élevé sur « chat », la représentation $h$ d'une photo de chat doit donc pointer vers $a_{\text{chat}}$. L'entraînement tire chaque photo de chat vers $a_{\text{chat}}$ et l'éloigne des autres classes : les photos de chat finissent proches les unes des autres.

# Exemple

- Prédire la lettre suivante d'un nom : une classe par lettre.
- Prédire le mot suivant : une classe par mot du vocabulaire $V$, soit $K = |V|$ classes, des dizaines de milliers ; le [[Fonction softmax|softmax]] porte alors sur tout le vocabulaire et l'[[Entropie croisée multi-classe|entropie croisée]] sur le vrai mot suivant.

# Remarque

Les vecteurs $a_c$ sont eux aussi des plongements : un vecteur par classe. C'est le même score linéaire par classe que dans la [[Régression logistique multinomiale]], dont le [[Fonction softmax|softmax]] normalise les sorties. Les mots reçoivent de la même façon des vecteurs du côté de l'entrée, par une [[Couche de plongement]].

#ml-1

# Définition

Un [[Perceptron multicouche|perceptron multicouche]] transforme son entrée étape par étape :

$$x \longrightarrow f_1 \longrightarrow h^{(1)} \longrightarrow f_2 \longrightarrow h^{(2)} \longrightarrow \cdots \longrightarrow h^{(n)} \longrightarrow \underset{\text{formats the output}}{f_{\text{out}}} \longrightarrow \hat{y}$$

Les états intermédiaires $h^{(1)}, \dots, h^{(n)}$ sont des représentations de $x$ : des **plongements** (*embeddings*).

La dernière couche ne fait que **formater** la sortie : une couche linéaire, puis une sigmoïde, un [[Fonction softmax|softmax]] ou rien. Tout ce qui précède construit la représentation de $x$.

# Interprétation

Un plongement est donc la façon dont le réseau voit une entrée : ce n'est pas la sortie, mais l'état interne à partir duquel la sortie se calcule.

Les entrées qui doivent produire la même sortie doivent recevoir des représentations **proches**. La dernière couche d'un classifieur s'écrit

$$z_c = h \cdot a_c + b_c$$

avec un vecteur $a_c$ par classe (voir [[Un vecteur par classe]]). Un produit scalaire est grand lorsque les deux vecteurs pointent dans le **même sens** : pour obtenir un score élevé sur « chat », la représentation $h$ d'une photo de chat doit pointer vers $a_{\text{chat}}$. L'entraînement tire alors chaque photo de chat vers $a_{\text{chat}}$ et l'éloigne des autres classes, si bien que les photos de chat finissent proches les unes des autres.

Les vecteurs $a_c$ sont eux aussi des plongements : un vecteur par classe. La proximité des représentations se lit avec les [[Mesures de similarité et de distance]].

# Exemple

Le [[Problème du ou exclusif|problème du ou exclusif]] l'illustre déjà : dans l'espace des couches cachées, une seule droite suffit à séparer les classes, alors qu'aucune droite ne les sépare dans l'espace d'entrée. La couche cachée change l'espace, et c'est cette nouvelle représentation qui rend la tâche linéaire.

# Remarque

L'état caché $h_t$ d'un [[Réseau récurrent]] est un plongement du préfixe : il résume $x_1, \dots, x_t$ et représente donc une portion de séquence, pas seulement une entrée isolée.

La notion se retrouve à l'entrée avec la [[Couche de plongement]], qui apprend un vecteur par symbole, et sans étiquette avec l'[[Auto-encodeur]], qui apprend une représentation compacte en imposant un goulot d'étranglement.

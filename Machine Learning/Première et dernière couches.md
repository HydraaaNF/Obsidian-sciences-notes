#ml-1

# Modèle

La taille des entrées et celle des sorties fixent les dimensions des deux couches extrêmes d'un [[Perceptron multicouche]] ; les couches intermédiaires restent libres.

- La taille de l'entrée $x$ est connue : la première couche transforme $\dim(x)$ valeurs en $n_1$ neurones.
- La taille de la sortie $y$ est connue : la dernière couche transforme $n_k$ neurones en $\dim(y)$ valeurs.
- Le domaine de $y$ est connu : la dernière activation doit produire exactement ce domaine.

Le choix de l'activation de sortie suit donc le domaine de $y$ :

- $y \in \mathbb{R}$ : aucune activation, la dernière couche reste linéaire.
- $y \in (0, 1)$, une probabilité : sigmoïde, ou aucune activation si la perte `BCEWithLogitsLoss` intègre elle-même la sigmoïde.
- $y \geq 0$ : ReLU, softplus.
- Une classe parmi $K$ : softmax (voir [[Types de classification]]).

# Remarque

Le cas binaire est un cas particulier des deux autres types de classification : une seule sigmoïde, ou un softmax sur deux scores. Les deux écritures décrivent la même famille de modèles ; la section des [[Types de classification]] donne pour chaque cas le nombre de sorties, la perte et la règle de décision associées.

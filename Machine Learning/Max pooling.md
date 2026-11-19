#ml-2

# Définition

Le **max pooling** est une opération d'agrégation appliquée à une carte d'activations. Une fenêtre glisse sur la carte par pas régulier et, dans chaque fenêtre, seule la valeur maximale est conservée ; la sortie est une carte de résolution réduite dont chaque cellule résume une fenêtre de l'entrée.

Trois éléments caractérisent l'opération :

- la **taille de fenêtre**, par exemple $2 \times 2$ ;
- le **pas**, distance entre deux positions successives de la fenêtre ;
- la **règle de sélection**, le maximum, que des variantes remplacent par le minimum ou la moyenne.

Aucun poids n'intervient dans ce calcul : l'opération compare et sélectionne, elle n'apprend rien.

# Propriétés

- **Réduction de la taille** : sur une carte $4 \times 4$ découpée en fenêtres $2 \times 2$ disjointes (pas de 2), la sortie est $2 \times 2$ ; chaque dimension est divisée par la taille de fenêtre.
- **Aucun paramètre appris** : contrairement à une [[Couche de convolution]], l'opération n'a ni poids ni biais à mettre à jour, elle n'ajoute donc rien au nombre de paramètres du modèle.
- **Robustesse aux petits décalages** : une légère translation de l'entrée laisse le maximum d'une fenêtre inchangé tant que le même pic y reste, la sortie varie donc peu.
- **Variantes** : le minimum et la moyenne sur chaque fenêtre suivent le même principe de fenêtre glissante, seule la règle de sélection change.

# Exemple

Sur la matrice $4 \times 4$ suivante, avec des fenêtres $2 \times 2$ et un pas de 2 :

$$
\begin{bmatrix}
1 & 3 & 2 & 1 \\
4 & 2 & 0 & 1 \\
5 & 1 & 2 & 6 \\
0 & 2 & 3 & 4
\end{bmatrix}
\xrightarrow{\max\ 2 \times 2}
\begin{bmatrix}
4 & 2 \\
5 & 6
\end{bmatrix}
$$

Chaque cellule de sortie est le maximum d'un quadrant :

- en haut à gauche, $\{1, 3, 4, 2\}$ donne $4$ ;
- en haut à droite, $\{2, 1, 0, 1\}$ donne $2$ ;
- en bas à gauche, $\{5, 1, 0, 2\}$ donne $5$ ;
- en bas à droite, $\{2, 6, 3, 4\}$ donne $6$.

Les quatre fenêtres recouvrent la totalité de l'entrée : seize valeurs sont résumées par quatre.

# Remarque

En PyTorch, l'opération s'écrit `torch.nn.MaxPool2d(2)` pour une fenêtre $2 \times 2$ ; le module agit sur un tenseur de [[Tenseurs PyTorch]] dont les deux dernières dimensions sont spatiales, et le pas vaut par défaut la taille de fenêtre, ce qui rend les fenêtres disjointes.

Le max pooling s'intercale entre les couches de convolution d'un [[Réseau de neurones convolutif]] : il réduit la résolution des cartes à chaque étage sans coût de paramètres, tandis que la [[Couche de convolution]] qui le précède porte, elle, les poids appris.

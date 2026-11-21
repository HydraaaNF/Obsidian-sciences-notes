#ml-2

# Définition

Le champ récepteur d'une sortie d'une pile de convolutions est le nombre d'échantillons d'entrée qui influencent cette sortie.

Pour une pile de [[Convolution dilatée|convolutions dilatées]] dont les dilatations sont $d_1, d_2, \dots, d_L$ et un noyau de taille $k$, il vaut

$$R = 1 + (k-1)\sum_{l=1}^{L} d_l$$

La somme porte sur toutes les convolutions comprises entre l'entrée et la sortie, convolution causale d'entrée incluse : pour $C$ couches résiduelles de $U$ unités chacune, elle compte donc $L = C \times U + 1$ convolutions (7 pour deux couches de trois unités, 16 pour trois couches de cinq unités).

# Propriétés

Pour une seule convolution de noyau $k$ et de dilatation $d$, la formule se réduit à $R = 1 + (k-1)d$.

En isolant la convolution causale d'entrée, de dilatation $1$, et en notant $S$ la somme des dilatations des couches résiduelles, la forme complète s'écrit

$$R = 1 + (k-1)(1 + S) = (S + 1)(k-1) + 1$$

Lorsque les $C$ couches résiduelles ont la même somme de dilatations $s$, la formule devient

$$R = (s \times C + 1)(k-1) + 1$$

où le $+1$ entre parenthèses est la contribution de la convolution causale d'entrée.

Dans une couche de $U$ unités dont les dilatations valent $1, 2, 4, \dots, 2^{U-1}$, la somme vaut $s = 2^{U} - 1$.

Le champ récepteur croît de façon exponentielle avec la profondeur lorsque les dilatations doublent d'une couche à l'autre, sans augmentation du nombre de paramètres : seule la portée des connexions change. Quand les couches répètent la même progression, chaque couche ajoute $s(k-1)$ au champ récepteur.

Les connexions résiduelles, de la forme $\mathbf{x} \mapsto \mathbf{x} + F(\mathbf{x})$, stabilisent l'entraînement lorsque le nombre de couches augmente.

# Exemple

### Deux couches résiduelles de trois unités

Noyau $k = 2$, dilatations $1, 2, 4$ dans chaque couche.

Somme des dilatations d'une couche :

$$1 + 2 + 4 = 7$$

Somme des dilatations des deux couches :

$$7 \times 2 = 14$$

Contribution de la convolution causale d'entrée, de dilatation $1$ :

$$(k-1) \times 1 = (2-1) \times 1 = 1$$

Champ récepteur :

$$R = 1 + (2-1)(1 + 14) = 1 + 15 = 16$$

Sous la forme condensée :

$$R = (7 \times 2 + 1)(2-1) + 1 = 15 \times 1 + 1 = 16$$

### Trois couches résiduelles de cinq unités

Noyau $k = 2$, dilatations $1, 2, 4, 8, 16$ dans chaque couche.

Somme des dilatations d'une couche :

$$1 + 2 + 4 + 8 + 16 = 31$$

Somme des dilatations des trois couches :

$$31 \times 3 = 93$$

Champ récepteur :

$$R = 1 + (2-1)(1 + 93) = 1 + 94 = 95$$

Sous la forme condensée :

$$R = (31 \times 3 + 1)(2-1) + 1 = 94 + 1 = 95$$

### Lecture du schéma d'une pile

Le schéma d'une pile de deux couches résiduelles de trois unités se lit de bas en haut :

- les cercles du bas sont les échantillons d'entrée ;
- chaque rangée intermédiaire est une couche d'activations, reliée à la rangée inférieure par des flèches obliques dont la portée double à l'intérieur d'une couche, puis repart à $1$ pour la couche suivante ;
- le nœud encadré en haut à droite est l'échantillon suivant prédit, « Predicted next sample » ;
- le cône de dépendances qui remonte jusqu'à ce nœud matérialise le champ récepteur, c'est-à-dire l'ensemble des échantillons d'entrée qui pèsent sur la prédiction.

Pour la pile de six rangées correspondant à l'exemple des deux couches de trois unités, les dilatations valent, de haut en bas :

| Rangée | Dilatation |
| --- | --- |
| 1 | 4 |
| 2 | 2 |
| 3 | 1 |
| 4 | 4 |
| 5 | 2 |
| 6 | 1 |

# Interprétation

Le champ récepteur mesure la profondeur de passé qu'une sortie consulte. Plus il est grand, plus le modèle peut relier un échantillon à des événements lointains de la séquence.

La dilatation est le levier qui permet cette croissance à coût constant : à noyau fixé, une pile de couches aux dilatations $1, 2, 4, 8, \dots$ double la portée à chaque étage, alors qu'une pile de convolutions non dilatées ne la fait croître que linéairement.

Dans une pile causale comme [[Architecture WaveNet]], cette portée se lit directement sur la fenêtre d'entrée utilisée pour prédire un échantillon, et fixe donc la fenêtre d'échantillons passés utilisée pour calculer la perte, détaillée dans [[Entraînement de WaveNet]].

Ce champ récepteur borne aussi la fenêtre de contexte lue à chaque pas d'[[Inférence autorégressive]].

# Remarque

Une première évaluation du champ récepteur omet souvent la convolution causale d'entrée : avec deux couches de trois unités et un noyau $k = 2$, la formule $R = \text{somme des dilatations} \times \text{nombre de couches} \times (k-1) + 1$ donne $(1+2+4) \times 2 \times (2-1) + 1 = 15$. Cette valeur omet la couche d'entrée ; en la comptant, $R = (7 \times 2 + 1)(2-1) + 1 = 16$. Le même oubli donne $94$ au lieu de $95$ pour trois couches de cinq unités. Il faut compter toutes les convolutions entre l'entrée et la sortie.

Le nombre de couches et le nombre d'unités par couche sont deux grandeurs distinctes : on note ici $C$ le nombre de couches résiduelles et $U$ le nombre d'unités d'une couche.

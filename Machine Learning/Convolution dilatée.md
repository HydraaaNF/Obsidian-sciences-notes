#ml-2

# Définition

Une **convolution dilatée** (*dilated convolution*) est une [[Convolution en une dimension|convolution]] dont le noyau n'est pas appliqué à des cellules contiguës de l'entrée, mais à des cellules espacées d'un pas constant $d$, appelé **dilatation**.

- $k$ : nombre d'éléments du noyau (le nombre de poids reste $k$) ;
- $\mathbf{w} = (w_1, \dots, w_k)$ : poids du noyau ;
- $b$ : biais ;
- $d$ : dilatation, entier supérieur ou égal à $1$ ;
- $x_1, \dots, x_n$ : entrée, éventuellement complétée par du [[Padding, stride et dilation|padding]] ;
- $s$ : stride.

Le noyau dilaté couvre $d(k-1)+1$ cellules d'entrée : c'est sa **taille effective**. Chaque sortie s'écrit, pour $i = 1, \dots, n_{\text{out}}$ :

$$y_i = \sum_{j=1}^{k} w_j\, x_{i+(j-1)d} + b$$

Le nombre de sorties $n_{\text{out}}$ se calcule avec cette taille effective à la place de $k$, selon la formule donnée dans [[Taille de sortie d'une convolution]] :

$$n_{\text{out}} = \left\lfloor \frac{n + 2p - d\,(k-1) - 1}{s} \right\rfloor + 1$$

# Interprétation

La dilatation augmente le champ couvert par le noyau sans ajouter de paramètre : les $k$ poids sont inchangés, mais la fenêtre s'étale sur $d(k-1)+1$ cellules.

Les cellules lues par une même sortie sont espacées de $d$, et à stride $1$ deux sorties voisines ne partagent aucune cellule dès que $d \ge 2$ : le réseau accède ainsi à un contexte plus large avec le même nombre de poids. C'est le mécanisme employé par les piles de couches à dilatation croissante de [[Dilatation des convolutions de WaveNet|WaveNet]], et combiné au padding à gauche dans la [[Convolution causale]].

Pour $d = 1$, la taille effective vaut $k$ et la convolution dilatée se réduit à la [[Convolution en une dimension]].

# Exemple

### Convolution dilatée sans biais

Entrée $x = (1,\,4,\,2,\,1,\,1)$, noyau $w = (w_1,\,w_2) = (1,\,2)$, $k = 2$, $d = 2$, padding $0$, stride $1$, biais nul.

Le noyau couvre $d(k-1)+1 = 3$ cellules, et l'entrée de longueur $5$ laisse trois positions de départ :

$$n_{\text{out}} = \left\lfloor \frac{5 - 2\,(2-1) - 1}{1} \right\rfloor + 1 = 3$$

Chaque sortie combine une cellule de la fenêtre avec $w_1$ et la cellule située deux rangs plus loin avec $w_2$ :

- $y_1 = x_1 w_1 + x_3 w_2 = 1 \times 1 + 2 \times 2 = 5$ ;
- $y_2 = x_2 w_1 + x_4 w_2 = 4 \times 1 + 1 \times 2 = 6$ ;
- $y_3 = x_3 w_1 + x_5 w_2 = 2 \times 1 + 1 \times 2 = 4$.

La sortie est donc $y = (5,\,6,\,4)$.

La position de chaque poids dans la fenêtre se lit sur ce tableau : une colonne par cellule d'entrée, une ligne par sortie, et l'écart de deux colonnes entre $w_1$ et $w_2$ matérialise la dilatation.

| Poids appliqué | $x_1$ | $x_2$ | $x_3$ | $x_4$ | $x_5$ |
|:---:|:---:|:---:|:---:|:---:|:---:|
| en $y_1$ | $w_1$ | | $w_2$ | | |
| en $y_2$ | | $w_1$ | | $w_2$ | |
| en $y_3$ | | | $w_1$ | | $w_2$ |

### Convolution dilatée avec stride

Mêmes entrée, noyau et dilatation, avec un stride $s = 2$ et toujours un padding nul.

La fenêtre ne démarre plus qu'aux positions $1$ et $3$, ce qui donne deux sorties :

$$n_{\text{out}} = \left\lfloor \frac{5 - 2\,(2-1) - 1}{2} \right\rfloor + 1 = 2$$

- $y_1 = x_1 w_1 + x_3 w_2 = 1 \times 1 + 2 \times 2 = 5$ ;
- $y_2 = x_3 w_1 + x_5 w_2 = 2 \times 1 + 1 \times 2 = 4$.

La sortie est donc $y = (5,\,4)$.

La dilation fixe l'écart entre les cellules lues par le noyau, le stride fixe le déplacement de la fenêtre d'une sortie à la suivante : les deux pas se composent sans se confondre.

### Convolution dilatée avec biais

Mêmes entrée ($x = (1,\,4,\,2,\,1,\,1)$), noyau ($w_1 = 1$, $w_2 = 2$), stride $1$ et dilatation $2$, avec un biais $b = 1$.

Le biais s'ajoute à chaque position, après la somme pondérée :

- $y_1 = x_1 w_1 + x_3 w_2 + b = 1 \times 1 + 2 \times 2 + 1 = 6$ ;
- $y_2 = x_2 w_1 + x_4 w_2 + b = 4 \times 1 + 1 \times 2 + 1 = 7$ ;
- $y_3 = x_3 w_1 + x_5 w_2 + b = 2 \times 1 + 1 \times 2 + 1 = 5$.

La sortie est donc $y = (6,\,7,\,5)$.

### Convolution dilatée avec padding

Mêmes noyau, biais nul, stride $1$ et dilatation $2$, avec un padding de $1$ des deux côtés : l'entrée devient $x = (0,\,1,\,4,\,2,\,1,\,1,\,0)$.

L'entrée complétée compte $7$ cellules, d'où $5$ positions de fenêtre :

$$n_{\text{out}} = \left\lfloor \frac{7 - 2\,(2-1) - 1}{1} \right\rfloor + 1 = 5$$

- $y_1 = x_1 w_1 + x_3 w_2 = 0 \times 1 + 4 \times 2 = 8$ ;
- $y_2 = x_2 w_1 + x_4 w_2 = 1 \times 1 + 2 \times 2 = 5$ ;
- $y_3 = x_3 w_1 + x_5 w_2 = 4 \times 1 + 1 \times 2 = 6$ ;
- $y_4 = x_4 w_1 + x_6 w_2 = 2 \times 1 + 1 \times 2 = 4$ ;
- $y_5 = x_5 w_1 + x_7 w_2 = 1 \times 1 + 0 \times 2 = 1$.

La sortie est donc $y = (8,\,5,\,6,\,4,\,1)$.

La fenêtre de $y_3$ combine $x_3 = 4$ et $x_5 = 1$, distants de deux rangs ; les deux zéros de padding n'entrent que dans $y_1$, à gauche, et dans $y_5$, à droite.

# Remarque

Le nombre de sorties ne doit pas être estimé sans tenir compte de la dilatation : pour $k = 2$ et $d = 2$, la fenêtre couvre $3$ cellules, non $2$. Une lecture qui ignore la dilatation conduit à des valeurs trop grandes, par exemple $9$ et $4$ au lieu de $5$ et $4$ pour l'exemple à stride $2$.

Une erreur fréquente dans le calcul de la première sortie avec padding consiste à décaler la fenêtre d'un rang : l'écriture $1 \times 1 + 2 \times 0 = 1$ omet la dilatation. Les cellules lues, aux rangs $1$ et $3$, valent $0$ et $4$, d'où $0 \times 1 + 4 \times 2 = 8$.

Enfin, chaque produit s'écrit dans l'ordre cellule puis poids, en suivant l'ordre de la fenêtre : $x_4 w_1 + x_6 w_2 = 2 \times 1 + 1 \times 2 = 4$. L'écriture inverse, $1 \times 2 + 2 \times 1$, donne le même nombre puisque la multiplication est commutative, mais elle échange cellule et poids dans chaque produit ; l'ordre cellule puis poids est retenu ici pour que chaque terme suive l'ordre de la fenêtre.

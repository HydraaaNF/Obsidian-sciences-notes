#ml-2

# Définition

Le **padding**, le **stride** et la **dilation** sont les trois paramètres d'une [[Convolution en deux dimensions|convolution en deux dimensions]] qui règlent le déplacement du noyau sur l'entrée et, par là, la taille de la sortie. On note $p$ le padding, $s$ le stride et $d$ la dilation.

Le **padding** $p$ est le nombre de couronnes de zéros ajoutées autour de l'entrée. Il agrandit la carte d'entrée de $2p$ cellules dans chaque dimension et sert à contrôler la taille de sortie.

Le **stride** $s$ est le pas de déplacement du noyau entre deux positions successives. Un stride $s=2$ sous-échantillonne la sortie, qui devient environ deux fois plus petite dans chaque dimension.

La **dilation** $d$ est l'espacement entre les cellules du noyau. Une dilation $d=2$ écarte les poids d'une cellule et élargit ainsi le champ récepteur sans augmenter le nombre de paramètres.

# Propriétés

La taille de sortie se déduit de ces trois paramètres par la formule de [[Taille de sortie d'une convolution|taille de sortie d'une convolution]] : pour une entrée $n \times n$, un noyau $k \times k$, un padding $p$, un stride $s$ et une dilation $d$,

$$n_{\text{out}} = \left\lfloor \frac{n + 2p - d\,(k-1) - 1}{s} \right\rfloor + 1$$

Chaque paramètre agit sur un terme distinct :

- le padding ajoute $2p$ cellules au numérateur, donc agrandit la sortie, exactement de $2p$ positions quand $s=1$ ;
- le stride divise le nombre de positions disponibles, donc réduit la sortie d'un facteur proche de $s$ ;
- la dilation remplace la taille $k$ du noyau par la taille effective $d(k-1)+1$, sans changer le nombre de poids.

# Exemple

Entrée $5 \times 5$, noyau $3 \times 3$, quatre configurations.

Sans padding, sans stride et sans dilation ($p=0$, $s=1$, $d=1$) :

$$n_{\text{out}} = 5 - 3 + 1 = 3$$

La sortie est $3 \times 3$ : chaque dimension perd $k-1 = 2$ cellules.

Avec un padding de deux cellules ($p=2$, $s=1$, $d=1$), l'entrée est entourée de deux couronnes de zéros et passe à $9 \times 9$ :

$$n_{\text{out}} = 9 - 3 + 1 = 7$$

La sortie est $7 \times 7$ : le padding $2$ fait gagner deux cellules de marge de chaque côté.

Avec un stride de deux ($p=0$, $s=2$, $d=1$) :

$$n_{\text{out}} = \left\lfloor \frac{5-3}{2} \right\rfloor + 1 = 2$$

La sortie est $2 \times 2$ : seules les positions de départ $1$ et $3$ sont visitées.

Avec une dilation de deux ($p=0$, $s=1$, $d=2$), le noyau effectif mesure $d(k-1)+1 = 2 \cdot 2 + 1 = 5$ cellules. Sur l'entrée $5 \times 5$, il ne reste qu'une position :

$$n_{\text{out}} = 5 - 4 = 1$$

Sur une entrée $7 \times 7$, la même configuration donne $7 - 4 = 3$, soit une sortie $3 \times 3$.

# Remarque

Un padding de $p$ cellules se dessine avec $p$ couronnes de zéros de chaque côté. Pour $p=2$ sur une entrée $5 \times 5$, la grille effective compte donc $9 \times 9$ cellules et la sortie $7 \times 7$ ; une représentation à une seule couronne, avec une sortie $5 \times 5$, correspond à $p=1$. Confondre le nombre de couronnes avec le nombre de cellules ajoutées de chaque côté est une erreur fréquente de lecture du paramètre.

La dilation ne modifie pas le nombre de poids du noyau : elle ne fait qu'espacer leurs positions. Le noyau effectif $d(k-1)+1$ croît avec $d$, ce qui élargit le champ récepteur d'une [[Convolution dilatée|convolution dilatée]] sans coût de paramètres supplémentaire.

Le padding conserve la taille de sortie quand $s=1$ et $p=(k-1)/2$ : c'est le réglage usuel d'une [[Couche de convolution|couche de convolution]] qui doit renvoyer une carte de même dimension que son entrée.

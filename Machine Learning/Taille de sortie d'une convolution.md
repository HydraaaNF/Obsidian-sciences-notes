#ml-2

# Définition

La **taille de sortie** d'une [[Couche de convolution|convolution]] se calcule à partir de la taille d'entrée, de la taille du noyau et des paramètres de [[Padding, stride et dilation|padding, de stride et de dilation]].

La dilation espace les éléments du noyau : un noyau de $k$ éléments régulièrement espacés de $d$ positions couvre $d(k-1)+1$ cellules d'entrée. Cette quantité est la **taille effective du noyau**, et c'est elle qui remplace $k$ dans le calcul.

Pour une entrée carrée $n \times n$, un noyau $k \times k$, un padding $p$, un stride $s$ et une dilation $d$ :

$$n_{\text{out}} = \left\lfloor \frac{n + 2p - d\,(k-1) - 1}{s} \right\rfloor + 1$$

En une dimension, pour une entrée de longueur $L_{\text{in}}$ et un noyau de longueur $k$ :

$$L_{\text{out}} = \left\lfloor \frac{L_{\text{in}} + 2p - d\,(k-1) - 1}{s} \right\rfloor + 1$$

# Interprétation

Le numérateur $n + 2p - d(k-1) - 1$ s'écrit $(n + 2p) - (d(k-1)+1)$ : l'entrée gagne $2p$ cellules avec le padding, et l'on en retranche la taille effective du noyau. La différence mesure la marge laissée à la position de départ du noyau dans l'entrée agrandie.

La division par $s$ puis l'arrondi par défaut donnent le nombre d'écarts de $s$ positions entre départs successifs, et le $+1$ rétablit la position de départ.

La longueur de sortie diffère en général de la longueur d'entrée : une entrée de longueur $24$ convolée par un noyau de taille $3$ donne $22$ positions, et non $24$. C'est ce qui distingue la convolution des opérations qui conservent la [[Forme d'un tenseur|forme]] de l'entrée.

# Propriétés

Cas particuliers de la formule générale, pour un noyau $3 \times 3$ :

- sans padding ($p=0$), sans stride ($s=1$) et sans dilation ($d=1$) : $n_{\text{out}} = n - 2$ ;
- avec un padding $p=2$ : l'entrée est entourée de deux couronnes de zéros et $n_{\text{out}} = n + 2$ ;
- avec un stride $s=2$ : $n_{\text{out}} = \left\lfloor \frac{n-3}{2} \right\rfloor + 1$ ;
- avec une dilation $d=2$ : le noyau effectif est de taille $5 \times 5$ et $n_{\text{out}} = n - 4$.

En une dimension, sans padding, sans stride et sans dilation, la formule se réduit à la longueur d'entrée moins la taille du noyau plus un :

$$L_{\text{out}} = L_{\text{in}} - k + 1$$

# Exemple

Une [[Convolution en une dimension|convolution en une dimension]] sur une entrée de longueur $24$, avec un noyau $k=3$, un canal d'entrée et deux filtres distincts, produit deux cartes de sortie de longueur $22$ chacune : la sortie a pour [[Forme d'un tenseur|forme]] $22 \times 2$.

$$L_{\text{out}} = 24 - 3 + 1 = 22$$

Une convolution dilatée en une dimension, avec $k=2$, les poids $w_1=1$ et $w_2=2$, un biais nul, $p=0$, $s=1$ et $d=2$, appliquée à l'entrée $x = (1,\,4,\,2,\,1,\,1)$, donne une sortie de longueur $3$ :

$$n_{\text{out}} = \left\lfloor \frac{5 - 2\,(2-1) - 1}{1} \right\rfloor + 1 = 3$$

La dilation de $2$ espace les deux poids du noyau de deux positions sur l'entrée, si bien que les fenêtres successives sont $(x_1,x_3)$, $(x_2,x_4)$ et $(x_3,x_5)$ :

- $y_1 = 1 \times 1 + 2 \times 2 = 5$ ;
- $y_2 = 4 \times 1 + 1 \times 2 = 6$ ;
- $y_3 = 2 \times 1 + 1 \times 2 = 4$.

La sortie est donc $y = (5,\,6,\,4)$.

# Remarque

Pour le noyau $k=2$ et la dilation $d=2$ de l'exemple, l'écriture $\left\lfloor \frac{5 - 2 - (2-1)\times 1}{1} \right\rfloor + 1$ soustrait $k=2$ puis $(d-1)(k-1)=1$. Or $k + (d-1)(k-1) = d(k-1)+1$ : cette forme soustrait donc elle aussi la taille effective du noyau, et elle coïncide avec la formule générale pour tout $k$ et tout $d$.

Les deux écritures ne diffèrent que par le regroupement des termes : la formule générale isole $d(k-1)$ et le $1$, tandis que l'écriture de l'exemple regroupe la taille effective en $k + (d-1)(k-1)$. C'est cette même taille effective qui s'emploie pour la [[Convolution en deux dimensions|convolution en deux dimensions]] comme pour la convolution en une dimension.

- La [[Conservation de la longueur dans une convolution causale]] applique cette formule avec un padding à gauche de $d(k-1)$ pour ramener la sortie à la longueur d'entrée.

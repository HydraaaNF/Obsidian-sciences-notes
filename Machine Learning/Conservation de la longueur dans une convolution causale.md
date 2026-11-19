#ml-2

# Définition

Une [[Convolution causale|convolution causale]] appliquée à une séquence de longueur $T$ conserve cette longueur lorsque le padding placé à gauche vaut la taille effective du noyau moins un :

$$p = d\,(k-1)$$

où $k$ est le nombre d'éléments du noyau et $d$ sa dilatation. La taille effective du noyau vaut $d(k-1)+1$, et $d(k-1)$ est exactement le nombre de cellules dont la fenêtre déborde à gauche de la position courante.

# Propriétés

La condition se déduit de la formule de la [[Taille de sortie d'une convolution]], écrite pour un stride $s=1$ et un padding asymétrique de $p$ cellules à gauche seulement :

$$L_{\text{out}} = L_{\text{in}} + p - d\,(k-1)$$

L'égalité $L_{\text{out}} = L_{\text{in}}$ impose donc $p = d(k-1)$, soit un padding à gauche égal à la taille effective du noyau moins un.

Les cas extrêmes se lisent sur la même formule :

- sans padding ($p=0$), la sortie perd $d(k-1)$ cellules ;
- avec un noyau de deux éléments ($k=2$), la perte vaut $d$ et une entrée de [[Forme d'un tenseur|forme]] $[B, C, T]$ donne une sortie $[B, C, T-d]$ ;
- avec $p = d(k-1)$, la sortie retrouve la forme $[B, C, T]$ de l'entrée.

# Interprétation

Le padding causal ajoute $d(k-1)$ zéros avant la première cellule de la séquence. Chaque position de sortie dispose alors de toute sa fenêtre tournée vers le passé, sans jamais lire de cellule future, et le nombre de positions reste celui de l'entrée : la sortie est alignée pas à pas sur elle.

L'alternative consiste à rogner l'entrée : on conserve ses $T-d(k-1)$ derniers pas, les plus récents, pour retrouver une longueur compatible avec celle de la sortie. Pour le noyau $k=2$ employé par WaveNet, cela revient à garder les $T-d$ derniers pas. Le padding est préféré dans une pile de convolutions, car il conserve toutes les positions et permet d'additionner directement l'entrée et la sortie.

# Remarque

Dans les piles de convolutions de type [[Architecture WaveNet|WaveNet]], chaque unité additionne le raccourci d'entrée $\mathbf{x}$ et la sortie $\mathbf{z}'$ de la convolution dilatée. Sans padding, $\mathbf{x}$ est de forme $[B, C, T]$ et $\mathbf{z}'$ de forme $[B, C, T-d]$ : l'addition serait impossible en l'état.

Le padding à gauche de $d(k-1)$ cellules, soit $d$ pour le noyau $k=2$ employé par WaveNet, rend chaque couche conservatrice de longueur. Les additions résiduelles restent valides à toutes les profondeurs, et l'empilement de nombreuses couches ne raccourcit pas la séquence.

Une convolution $1 \times 1$ placée en sortie ramène le nombre de canaux à celui de $\mathbf{x}$. L'axe des canaux $C$ est ainsi rétabli par cette convolution, l'axe temporel $T$ l'ayant été par le padding de $d(k-1)$ cellules : la forme complète $[B, C, T]$, condition de la somme $\mathbf{x} + \mathbf{z}'$, résulte des deux.

Le padding est unilatéral : un padding symétrique laisserait la fenêtre déborder à droite et briserait la causalité, en faisant dépendre une sortie de cellules futures.

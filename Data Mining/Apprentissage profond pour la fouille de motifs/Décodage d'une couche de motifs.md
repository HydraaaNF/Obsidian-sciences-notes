#dmv-pattern_mining_vs_deep_learning

# Définition

Le décodage d'une [[Couche de motifs]] reconstruit une transaction à partir du vecteur binaire qui marque les motifs actifs de la couche : son entrée latente est $y \in \{0,1\}^k$, avec $k$ nœuds en entrée et $m$ nœuds en sortie.

$$f_D(y) = \lambda_D\left(y\, W_b\right)$$

Le produit emploie la matrice de poids binaires $W_b$, qui compte $k$ lignes, une par neurone de motif, et $m$ colonnes, une par item : la sortie retrouve la largeur $m$ de l'entrée de l'encodeur.

La fonction de sortie ramène chaque pré-activation à une valeur binaire par bornage puis arrondi :

$$\lambda_D(x) = \operatorname{round}\left(\operatorname{clamp}(x)\right)$$

# Propriétés

Le produit matriciel détaille la pré-activation de chaque neurone de sortie :

$$(y\, W_b)_j = \sum_{i=1}^{k} y_i\, (W_b)_{i,j}$$

Comme $y$ et $W_b$ sont binaires, cette somme est entière et compte les motifs actifs qui contiennent l'item $j$.
Le [[Fonction de bornage dans un intervalle|bornage]] écrête les pré-activations supérieures à $1$ : un seul motif actif contenant l'item suffit donc à le reconstruire.
L'arrondi laisse $0$ à zéro et vaut $1$ dès que la pré-activation est positive : la sortie est la réunion des motifs actifs.

# Remarque

Le décodage est la réciproque de l'[[Encodage d'une transaction en motifs]] : les deux passes emploient la même matrice de poids, l'encodage la lisant transposée pour passer de $m$ items à $k$ motifs, le décodage la lisant dans l'autre sens pour revenir de $k$ motifs à $m$ items.

Un schéma de la passe avant annote $W_b^\top$ entre l'entrée et la couche de motifs, et $W_b$ entre cette couche et la sortie ; parcouru à rebours, dans le sens du décodage, il peut se lire comme une annotation $W_b^\top$ des connexions qui vont de la couche de motifs vers la sortie. La formule de décodage emploie $W_b$ sans transposée, et les dimensions tranchent : $y$ est de longueur $k$ et $W_b$ de taille $k \times m$, si bien que $y\, W_b$ rend un vecteur de longueur $m$, alors que $y\, W_b^\top$ multiplierait un vecteur de longueur $k$ par une matrice $m \times k$ et ne serait pas défini.

Les deux fonctions de sortie de la couche ne sont pas symétriques : celle de l'encodage ajoute un terme de biais avant le bornage, celle du décodage n'en comporte aucun.

Le vecteur latent est noté $y$, et $k$ désigne le nombre de motifs ; l'écriture $k \in \{0,1\}^k$, qui donne au vecteur le nom du paramètre fixant sa longueur, est une erreur fréquente : un vecteur binaire de longueur $k$ ne peut pas porter la lettre qui note ce nombre de motifs.

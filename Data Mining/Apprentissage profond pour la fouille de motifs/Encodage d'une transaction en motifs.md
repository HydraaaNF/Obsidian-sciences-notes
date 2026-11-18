#dmv-pattern_mining_vs_deep_learning

# Définition

L'encodage transforme une transaction binaire en l'état d'activation de la [[Couche de motifs]] : il projette l'entrée sur les $k$ neurones de motifs, puis quantifie le résultat en binaire.

L'entrée $s \in \{0,1\}^m$ est une transaction écrite comme un vecteur binaire de $m$ items, issue de [[Items, itemsets et base de transactions]] ; la sortie comporte une valeur binaire par neurone de motif.

La fonction d'encodage compose un produit par la matrice de poids binaires et une quantification :

$$f_E(s) = \lambda_E\left(s\, W_b^{\top}\right)$$

La matrice $W_b$ a $m$ colonnes et $k$ lignes, avec $m$ neurones en entrée et $k$ neurones en sortie.
La quantification $\lambda_E$ est l'activation appliquée au résultat du produit ; elle ajoute un biais $b_d$, borne la valeur dans $[0,1]$ et arrondit :

$$\lambda_E(z) = \operatorname{round}\left(\operatorname{clamp}\left(z + b_d\right)\right)$$

# Interprétation

L'encodage est la première moitié de la passe avant d'un [[Auto-encodeur de motifs]] : il fabrique la représentation de la transaction dans l'espace des motifs.

- $s$ est un vecteur ligne de $m$ composantes et $W_b^{\top}$ a $m$ lignes et $k$ colonnes, donc $s\,W_b^{\top}$ est un vecteur ligne de $k$ composantes, une par neurone de motif.
- Chaque colonne de $W_b^{\top}$, c'est-à-dire chaque ligne de $W_b$, est le motif porté par un neurone de la couche.
- Les poids étant binaires, une composante de $s\,W_b^{\top}$ compte les items du motif correspondant présents dans la transaction.
- Le biais $b_d$ décale ce compte : il fixe le seuil à partir duquel un neurone de motif doit s'activer.
- Le bornage, qui est la [[Fonction de bornage dans un intervalle]], ramène la valeur décalée dans $[0,1]$ ; l'arrondi la tranche ensuite entre $0$ et $1$, de sorte que la sortie est bien une activation binaire.

# Remarque

Le biais de l'encodage est noté $b_d$, avec l'indice du côté décodage, alors que la matrice de poids de l'encodage porte l'indice $b$ : l'indice du biais ne suit pas celui de la matrice qu'il accompagne.
La formule est conservée telle quelle ; un indice cohérent avec l'encodage serait $b_e$.

Les notations ne sont pas non plus homogènes entre l'encodage et le [[Décodage d'une couche de motifs|décodage]] : la matrice de poids y apparaît transposée d'un côté et non transposée de l'autre, et seul l'encodage ajoute un biais avant la quantification.
Ces conventions se lisent formule par formule et ne forment pas un système de notation unique.

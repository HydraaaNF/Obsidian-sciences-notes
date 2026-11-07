#ml-1

# Définition

Composer deux couches linéaires consiste à enchaîner deux transformations affines, en prenant la sortie de la première comme entrée de la seconde. En notant $x$ l'entrée vue comme une ligne, $A_1$ et $b_1$ les paramètres de la première couche, $A_2$ et $b_2$ ceux de la seconde :

$$h = xA_1^\top + b_1$$

$$\hat{y} = hA_2^\top + b_2$$

# Propriétés

La composition de couches linéaires se réduit à une seule couche linéaire. En substituant $h$ dans la seconde équation :

$$\hat{y} = x\underbrace{A_1^\top A_2^\top}_{A^\top} + \underbrace{b_1 A_2^\top + b_2}_{b}$$

Le résultat est encore de la forme $\hat{y} = xA^\top + b$ : une unique transformation affine, portée par une seule couche.

Empiler des couches linéaires ajoute donc des paramètres, mais aucune puissance d'expression. La profondeur ne devient utile que par la non-linéarité insérée **entre** les couches, voir [[Fonctions d'activation]] et [[Perceptron multicouche]].

### Démonstration

On part de la composition :

$$h = xA_1^\top + b_1$$

$$\hat{y} = hA_2^\top + b_2$$

On remplace $h$ par son expression dans la seconde ligne :

$$\hat{y} = (xA_1^\top + b_1)A_2^\top + b_2$$

On développe :

$$\hat{y} = xA_1^\top A_2^\top + b_1A_2^\top + b_2$$

Le produit $A_1^\top A_2^\top$ est une matrice, notée $A^\top$ ; la quantité $b_1A_2^\top + b_2$ est un vecteur, noté $b$. D'où :

$$\hat{y} = xA^\top + b$$

Les deux couches n'ont fait que définir de nouveaux paramètres $A$ et $b$ : la fonction calculée reste affine.

# Remarque

Un empilement de couches linéaires n'a pas plus de pouvoir qu'une régression linéaire, quel que soit le nombre de couches. C'est l'activation non linéaire placée entre les couches qui fait la différence, en permettant à la représentation intermédiaire de se déformer avant la couche suivante.

# Exemple

La démonstration sur le [[Problème du ou exclusif]] rend l'échec visible. Le jeu de données compte $200$ points bruités autour des quatre coins d'un carré.

- La [[Régression logistique]] ne progresse pas : sa perte stagne à $0.693 = \ln 2$ et le modèle répond $0.5$ partout, soit l'[[Entropie croisée binaire|entropie croisée]] d'un tirage à pile ou face.
- Deux couches linéaires sans activation donnent exactement le même résultat.
- Une couche cachée de deux neurones $\tanh$ résout le problème.
- En regardant à l'intérieur du réseau, une droite sépare alors les classes dans l'espace caché.

L'expérience invite à relancer avec d'autres graines d'initialisation, puis avec huit neurones cachés.

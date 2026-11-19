#ml-2

# Définition

Une convolution causale est une [[Convolution en une dimension]] dont le noyau est décalé vers le passé : le padding est appliqué à gauche uniquement, de sorte que la sortie à un instant donné ne dépende que des entrées passées et de l'entrée courante.

Pour un noyau de taille $3$ appliqué à une séquence temporelle $T_{-2}, T_{-1}, T_0, T_{+1}, T_{+2}$ :

- une convolution standard a une fenêtre centrée sur l'instant de sortie : la sortie en $T_0$ voit $T_{-1}$, $T_0$ et $T_{+1}$, donc le futur ;
- une convolution causale a une fenêtre décalée vers le passé : la sortie en $T_0$ ne voit que $T_{-2}$, $T_{-1}$ et $T_0$.

Aucun échantillon futur n'entre dans le calcul de la sortie courante.

# Exemple

### Convolution dilatée à padding causal

Entrée : $x = (1, 4, 2, 1, 1)$, prolongée à gauche par deux zéros, soit $x = (0, 0, 1, 4, 2, 1, 1)$.

Paramètres de la couche :

- convolution en une dimension, dilatation $2$, stride $1$ ;
- noyau $w = (w_1, w_2) = (1, 2)$, taille $k = 2$ ;
- pas de biais ;
- padding de $2$ **à gauche uniquement** (causal).

Le padding s'écrit `F.pad(x, (2, 0))`. Avec une dilatation de $2$, la sortie en position $t$ combine les entrées $x_{t-2}$ et $x_t$ :

$$y_t = 1 \times x_{t-2} + 2 \times x_t$$

Le vecteur de sortie, aligné sur les entrées, est $y = [0, 0, 2, 8, 5, 6, 4]$ :

| Position $t$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Entrée $x_t$ | 0 | 0 | 1 | 4 | 2 | 1 | 1 |
| Sortie $y_t$ | 0 | 0 | 2 | 8 | 5 | 6 | 4 |

Calcul de chaque sortie :

$$y_2 = 1 \times x_0 + 2 \times x_2 = 1 \times 0 + 2 \times 1 = 2$$

$$y_3 = 1 \times x_1 + 2 \times x_3 = 1 \times 0 + 2 \times 4 = 8$$

$$y_4 = 1 \times x_2 + 2 \times x_4 = 1 \times 1 + 2 \times 2 = 5$$

$$y_5 = 1 \times x_3 + 2 \times x_5 = 1 \times 4 + 2 \times 1 = 6$$

$$y_6 = 1 \times x_4 + 2 \times x_6 = 1 \times 2 + 2 \times 1 = 4$$

Les deux premières positions de $y$ ne portent pas de sortie calculée : la fenêtre du noyau y sortirait de la séquence. Elles sont notées $0$ et servent uniquement à aligner $y$ sur $x$ ; les sorties effectives occupent les positions $2$ à $6$.

# Interprétation

La causalité rend la couche utilisable pour la génération autorégressive, échantillon par échantillon : à chaque pas, la sortie ne peut être influencée que par ce qui a déjà été produit. C'est le choix retenu dans [[Architecture WaveNet]] pour la modélisation audio.

Une convolution standard, avec une fenêtre centrée, laisse la sortie « voir » le futur : elle convient à une classification ou à une modélisation non causale, mais pas à une génération séquentielle.

# Remarque

L'alignement de la colonne des sorties sur celle des entrées demande attention. Avec deux valeurs de padding à gauche, la première sortie calculée se place en position $2$, pas en position $0$ : écrire les sorties dès la première ligne décale toutes les valeurs d'une ligne et fait lire $y_0 = 2$ au lieu de $y_2 = 2$, en omettant les deux positions de tête.

Le noyau est simplement décalé dans le temps, sans changer le nombre de paramètres : la couche causalise la convolution à coût constant.

Le padding à gauche choisi ici préserve la longueur de la séquence, propriété détaillée dans [[Conservation de la longueur dans une convolution causale]]. La dilatation utilisée dans l'exemple relève de la [[Convolution dilatée]], et les rôles respectifs du padding, du stride et de la dilatation sont décrits dans [[Padding, stride et dilation]].

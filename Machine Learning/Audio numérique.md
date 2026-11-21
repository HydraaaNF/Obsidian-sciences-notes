#ml-2

# Définition

Un **son** est une onde de pression : l'air vibre et cette vibration se propage.

L'**audio numérique** est la représentation d'un tel signal par une suite finie de nombres, obtenue en deux étapes :

- l'**échantillonnage** : on relève une valeur toutes les $\frac{1}{f_s}$ secondes, où $f_s$ est la **fréquence d'échantillonnage** ;
- la **quantification** : chaque valeur relevée est arrondie à l'un des niveaux d'une grille finie, dont le nombre est fixé par la résolution en bits.

# Modèle

Le signal échantillonné et quantifié est modélisé comme une séquence unidimensionnelle de $T$ nombres :

$$x_1, x_2, \dots, x_T$$

où $x_t$ est l'amplitude quantifiée au $t$-ième instant d'échantillonnage, soit à l'instant $\frac{t}{f_s}$.

Chaque terme de la séquence est un scalaire : le signal est une suite de valeurs indexées par le temps, et non un ensemble non ordonné. Une convolution unidimensionnelle s'applique donc directement à cette entrée, voir [[Convolution en une dimension]].

# Exemple

Les ordres de grandeur usuels sont les suivants :

- parole : $f_s = 16$ kHz ;
- disque compact : $f_s = 44{,}1$ kHz ;
- quantification sur 16 bits, soit $2^{16} = 65\,536$ niveaux.

À $16$ kHz, une seconde d'audio compte $16\,000$ échantillons. La même durée lue à trois échelles montre la structure du signal :

- sur une seconde, la forme d'onde apparaît comme une enveloppe dense, dont les variations dessinent les syllabes ;
- sur 100 millisecondes, on distingue les oscillations locales de l'enveloppe ;
- sur 1 milliseconde, les échantillons individuels sont visibles, reliés par des segments : à cette échelle le signal se lit comme une suite de points, un point par échantillon.

Une grille d'échantillonnage se lit de la même façon sur une courbe d'amplitude en fonction du temps : la courbe continue du signal analogique est remplacée par des points régulièrement espacés de $\frac{1}{f_s}$, reliés verticalement à l'axe des temps.

# Remarque

L'audio brut est un cas particulier de [[Données séquentielles]] : la séquence générique est formée de vecteurs $x_t \in \mathbb{R}^n$, alors qu'un signal audio fournit un vecteur de dimension $n = 1$ à chaque pas. La longueur $T$ varie d'un enregistrement à l'autre, comme pour toute séquence.

La réduction du nombre de niveaux de quantification, de $65\,536$ à $256$ dans WaveNet, est l'objet de la [[Compression mu-law]] : elle ramène chaque amplitude sur une grille grossière.

La description retenue ici est purement temporelle, un échantillon après l'autre. Une description en temps-fréquence, qui résume le contenu spectral sur des fenêtres, est donnée par le [[Spectrogramme mel]].

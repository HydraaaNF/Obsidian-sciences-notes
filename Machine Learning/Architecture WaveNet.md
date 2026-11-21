#ml-2

# Modèle

WaveNet est un modèle génératif pour l'audio bâti sur des [[Convolution causale|convolutions causales]] en une dimension. Son architecture se lit en deux parties : un bloc résiduel qui transforme la séquence d'entrée, puis une tête de sortie qui agrège les sorties latérales des couches.

La séquence passe d'abord par une convolution causale d'entrée, placée juste avant le bloc résiduel.

Le bloc résiduel empile $k$ [[Unité résiduelle de WaveNet|unités résiduelles]]. Dans chaque unité :

- une [[Dilatation des convolutions de WaveNet|convolution dilatée]] traite l'entrée du bloc ;
- sa sortie traverse deux branches parallèles, une tangente hyperbolique et une sigmoïde ;
- les deux branches sont multipliées terme à terme ;
- une convolution $1 \times 1$ ramène le résultat à la dimension du bloc ;
- une addition avec l'entrée de l'unité, la connexion résiduelle, forme la sortie de l'unité.

La sortie de la convolution $1 \times 1$ de chaque unité alimente en outre une skip-connection. La tête de sortie agrège ces sorties latérales :

- les skip-connections sont sommées ;
- l'agrégat passe par une convolution $1 \times 1$ ;
- une tangente hyperbolique est appliquée ;
- une seconde convolution $1 \times 1$ produit les scores de sortie ;
- un softmax les transforme en distribution sur les échantillons audio.

# Propriétés

WaveNet est :

- un modèle sequence-to-sequence ;
- un modèle autorégressif ;
- un modèle causal ;
- un réseau à convolutions causales en une dimension ;
- un réseau à noyau de taille $2$ ;
- un modèle conditionné sur un vecteur $\mathbf{h}$, voir [[Conditionnement de WaveNet]].

Sa profondeur s'organise en $L$ couches résiduelles, chacune composée de $U$ unités résiduelles. Dans une couche, la dilatation de la $u$-ième unité vaut $2^{u-1}$ : les unités successives travaillent aux dilatations $1, 2, 4, 8, \dots$.

# Interprétation

La causalité de chaque convolution garantit qu'une sortie en un instant donné ne dépend que des échantillons passés et de l'échantillon courant. Le modèle peut donc être utilisé en génération autorégressive, un échantillon à la fois.

La dilatation croissante fait grandir le [[Champ récepteur d'une pile de convolutions|champ récepteur]] avec la profondeur tout en gardant un noyau de taille $2$ à chaque unité : les unités profondes consultent un passé lointain sans que le noyau grandisse. Le champ récepteur décrit l'étendue du passé consultée ; la causalité vient du padding appliqué à gauche dans chaque convolution.

La connexion résiduelle réinjecte l'entrée de chaque unité dans sa sortie, et les skip-connections donnent à la tête de sortie un accès direct aux représentations de toutes les profondeurs de la pile.

# Remarque

Le calcul du champ récepteur doit inclure la convolution causale d'entrée, placée avant le premier bloc résiduel : l'oublier sous-estime la portée temporelle du modèle.

Le schéma de l'architecture se lit comme une unité répétée $k$ fois dans un bloc résiduel ; une couche résiduelle est elle-même un empilement d'unités aux dilatations croissantes, et non une couche unique.

La [[Conservation de la longueur dans une convolution causale|conservation de la longueur]] fixe la contrainte de forme que doivent respecter les unités résiduelles du bloc, pour que l'addition résiduelle ait un sens.

WaveNet est un modèle autorégressif fondé sur la [[Décomposition autorégressive d'une densité|décomposition autorégressive d'une densité]], qui écrit la probabilité de la séquence comme un produit de conditionnelles.

L'[[Entraînement de WaveNet|entraînement de WaveNet]] apprend ces conditionnelles sur les codes audio, en parallèle sur toutes les positions grâce à la causalité.

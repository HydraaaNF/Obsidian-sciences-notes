#ml-3

# Définition

Dans chaque bloc du Transformer, un même petit réseau feed-forward, de type [[Perceptron multicouche]], est appliqué à chaque jeton pris séparément. Il enchaîne deux transformations linéaires séparées par une non-linéarité, choisie parmi les [[Fonctions d'activation]] :

$$\operatorname{FFN}(\mathbf{x}) = W_2 \operatorname{GELU}(W_1\mathbf{x}+\mathbf{b}_1)+\mathbf{b}_2$$

GELU est définie par $\operatorname{GELU}(x) = x\,\Phi(x)$, où $\Phi$ est la fonction de répartition de la loi normale centrée réduite.

# Modèle

La couche projette chaque vecteur de jeton vers une dimension interne plus large, puis revient à la dimension du modèle :

- entrée de dimension $1024$
- couche cachée de dimension $4096$
- sortie de dimension $1024$

soit le parcours $1024 \rightarrow 4096 \rightarrow 1024$, qui concentre environ deux tiers des paramètres du bloc.

Les poids sont partagés entre toutes les positions : le même réseau traite chaque jeton, sans rien échanger entre les positions.

La sous-couche est entourée d'une [[Connexions résiduelles|connexion résiduelle]] suivie d'une normalisation, notée `Add & Norm` :

$$\mathbf{x} \leftarrow \operatorname{Norm}\big(\mathbf{x} + \operatorname{FFN}(\mathbf{x})\big)$$

L'ensemble formé de l'attention puis du réseau feed-forward est empilé $N$ fois, voir [[Architecture du Transformer]].

# Interprétation

Les deux sous-couches du bloc se répartissent le travail :

- l'attention mélange les jetons : chaque position agrège de l'information venue des autres positions
- le réseau feed-forward transforme chaque jeton : il agit seul, position par position, et ne transporte aucune information d'une position à l'autre

Le bloc alterne donc un brassage horizontal, entre jetons, et une transformation verticale, à l'intérieur de chaque jeton.

# Remarque

La formule ci-dessus retient GELU, l'activation employée par les GPT ; ReLU occupe le même emplacement. Seule la non-linéarité change, pas sa place dans le bloc.

- Le [[Mélange d'experts]] généralise cette couche : le réseau feed-forward y est remplacé par plusieurs experts dont les sorties sont combinées.

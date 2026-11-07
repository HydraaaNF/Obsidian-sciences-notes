#ml-1

# Définition

Une connexion résiduelle ajoute l'entrée d'un bloc à sa sortie. Pour une entrée $x$ et un bloc de couches $F$ :

$$G(x) = F(x) + x$$

où $G$ est la sortie du bloc ainsi augmenté. Le bloc $F$ est typiquement un petit empilement de couches denses d'un [[Perceptron multicouche]], activations comprises.

# Interprétation

- Le bloc n'apprend que le **résidu** $F$, c'est-à-dire une correction de l'identité : la transformation identité n'a plus à être apprise.
- Le gradient remonte par le terme $+x$ sans être modifié : la rétropropagation dispose d'un chemin direct vers les couches précédentes.
- Conséquence : les réseaux très profonds deviennent entraînables, là où l'empilement de couches se heurte à la [[Disparition et explosion du gradient|disparition du gradient]].
- Dans le montage usuel, l'entrée $x$ se sépare en deux branches : une branche identité qui contourne le bloc, et une branche qui traverse les couches pour produire $F(x)$ ; les deux sorties sont additionnées pour donner $F(x) + x$.

# Remarque

- Les architectures à connexions résiduelles empilent couramment plus de cent cinquante couches (cent cinquante-deux pour ResNet).
- Chaque bloc d'un Transformer en comporte.
- La [[Mémoire à long et court terme|mémoire à long et court terme]] repose sur le même principe : son état est mis à jour par une addition, et non réécrit à travers une tangente hyperbolique.

$$c_t = f_t \odot c_{t-1} + i_t \odot \tilde{c}_t$$

- $c_t$ est l'état de cellule, mis à jour à partir de l'état précédent $c_{t-1}$ et d'un contenu nouveau $\tilde{c}_t$.
- $f_t$ et $i_t$ sont des portes comprises entre 0 et 1, appliquées composante par composante (produit terme à terme $\odot$).
- Quand $f_t$ est proche de 1 et $i_t$ proche de 0, $c$ est conservé tel quel, et son gradient aussi : l'addition laisse passer le gradient sur des centaines de pas.

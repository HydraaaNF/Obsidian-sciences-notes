#ml-1 #ml-3

# Définition

Une connexion résiduelle ajoute l'entrée d'un bloc à sa sortie. Pour une entrée $x$ et un bloc de couches $F$ :

$$G(x) = F(x) + x$$

où $G$ est la sortie du bloc ainsi augmenté. Le bloc $F$ est typiquement un petit empilement de couches denses d'un [[Perceptron multicouche]], activations comprises.

Dans un Transformer, la connexion résiduelle est une connexion de contournement (*skip connection*) à l'intérieur d'une couche : elle additionne l'entrée d'une sous-couche à la sortie de celle-ci. Elle exige que la sortie retrouve la forme de l'entrée, sans quoi la somme $T+\operatorname{MHA}(T)$ n'aurait pas de sens ; les sorties des huit têtes d'attention sont donc concaténées, ce qui redonne exactement la forme de $T$, avant l'addition.

# Interprétation

- Le bloc n'apprend que le **résidu** $F$, c'est-à-dire une correction de l'identité : la transformation identité n'a plus à être apprise.
- Le gradient remonte par le terme $+x$ sans être modifié : la rétropropagation dispose d'un chemin direct vers les couches précédentes.
- Conséquence : les réseaux très profonds deviennent entraînables, là où l'empilement de couches se heurte à la [[Disparition et explosion du gradient|disparition du gradient]].
- Dans le montage usuel, l'entrée $x$ se sépare en deux branches : une branche identité qui contourne le bloc, et une branche qui traverse les couches pour produire $F(x)$ ; les deux sorties sont additionnées pour donner $F(x) + x$.

# Remarque

- Les architectures à connexions résiduelles empilent couramment plus de cent cinquante couches (cent cinquante-deux pour ResNet).
- La [[Mémoire à long et court terme|mémoire à long et court terme]] repose sur le même principe : son état est mis à jour par une addition, et non réécrit à travers une tangente hyperbolique.
- Dans le décodeur, chaque sous-couche est suivie d'un *Add & Norm*, qui additionne l'entrée de la sous-couche puis normalise le résultat ; pour la couche feed-forward, cela s'écrit

  $$\mathbf{x} \leftarrow \operatorname{Norm}\big(\mathbf{x} + \operatorname{FFN}(\mathbf{x})\big)$$

L'[[Unité résiduelle de WaveNet]] en est une variante à activation à porte, où les branches tangente hyperbolique et sigmoïde se multiplient avant l'addition.

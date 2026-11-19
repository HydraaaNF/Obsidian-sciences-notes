#ml-2

# Définition

Une **unité résiduelle** de WaveNet transforme une séquence en enchaînant une [[Convolution dilatée|convolution dilatée]], une activation à porte, puis une convolution $1\times1$ dont la sortie est ajoutée à l'entrée de l'unité.

L'activation à porte combine deux convolutions parallèles, l'une filtrée par une tangente hyperbolique, l'autre par une sigmoïde :

$$\mathbf{z} = \tanh(W_{f,k} * \mathbf{x}) \odot \sigma(W_{g,k} * \mathbf{x})$$

- $\mathbf{x}$ : entrée de l'unité, de forme `[batch, canaux, temps]` ;
- $*$ : opérateur de convolution ;
- $\odot$ : produit terme à terme ;
- $k$ : indice de la couche ;
- $W_{f,k}$ : filtre de la branche $\tanh$ ;
- $W_{g,k}$ : filtre de la branche porte, dont la sortie passe par la sigmoïde $\sigma$.

Après la porte, une convolution $1\times1$ ramène $\mathbf{z}$ au nombre de canaux de $\mathbf{x}$, et le résultat est additionné à $\mathbf{x}$ par la [[Connexions résiduelles|connexion résiduelle]] qui contourne le bloc. La sortie de cette convolution $1\times1$, avant l'addition résiduelle, alimente aussi une connexion de saut, et les sorties ainsi collectées sont sommées avant la tête de sortie de l'[[Architecture WaveNet|architecture]].

# Interprétation

- La convolution dilatée lit l'entrée sur des positions espacées : le noyau reste de taille $K$, mais la dilatation étale sa fenêtre et fait accéder l'unité à un contexte temporel plus large.
- La branche $\tanh$ produit une amplitude signée, bornée entre $-1$ et $1$, qui porte le contenu du signal.
- La branche sigmoïde produit un coefficient borné entre $0$ et $1$, qui joue le rôle de porte et décide, canal par canal, de la fraction du contenu laissée passer.
- Le produit terme à terme applique cette porte à l'amplitude : un coefficient proche de $0$ éteint le canal, un coefficient proche de $1$ le laisse intact. Cette activation à porte remplace les activations usuelles, décrites dans [[Fonctions d'activation]].
- La convolution $1\times1$ mélange l'information entre canaux et rétablit le nombre de canaux de l'entrée, condition nécessaire à l'addition.
- L'addition par le raccourci laisse l'entrée traverser l'unité sans transformation : l'unité n'apprend qu'une correction, et le gradient dispose d'un chemin direct vers les couches amont.
- Les connexions de saut collectent la sortie de la convolution $1\times1$ de chaque unité pour la tête de sortie, qui les somme, applique une convolution $1\times1$, une $\tanh$, une autre convolution $1\times1$ et une [[Fonction softmax|softmax]].

# Modèle

Le conditionnement ajoute une information auxiliaire $\mathbf{h}$ aux deux pré-activations de la porte, dans chaque unité résiduelle.

Conditionnement global, avec un seul vecteur $\mathbf{h}$ pour tout le signal, par exemple l'identité du locuteur, identique à chaque pas de temps :

$$\mathbf{z} = \tanh\left(W_{f,k} * \mathbf{x} + V_{f,k}^{\top}\mathbf{h}\right) \odot \sigma\left(W_{g,k} * \mathbf{x} + V_{g,k}^{\top}\mathbf{h}\right)$$

Conditionnement local, avec une série temporelle $\mathbf{h}$ plus lente que l'audio, par exemple des traits linguistiques ou un [[Spectrogramme mel]] :

$$\mathbf{z} = \tanh\left(W_{f,k} * \mathbf{x} + V_{f,k} * \mathbf{h}\right) \odot \sigma\left(W_{g,k} * \mathbf{x} + V_{g,k} * \mathbf{h}\right)$$

- Dans le cas local, $\mathbf{h}$ est suréchantillonné au rythme de l'audio, par convolution transposée ou par répétition, et $V * \mathbf{h}$ est une convolution $1\times1$.
- $\mathbf{h}$ entre dans toutes les unités résiduelles : le conditionnement n'est pas appliqué à la seule entrée du réseau.
- La causalité ne concerne que $\mathbf{x}$ : $\mathbf{h}$ est connu d'avance, par exemple la phrase entière à prononcer, et peut être utilisé en entier sans attendre les pas de temps futurs.

Le détail des conditionnements est traité dans [[Conditionnement de WaveNet]].

# Remarque

- Sans padding, une convolution dilatée de noyau $K$ (taille du noyau, distincte de l'indice de couche $k$) et de dilatation $d$ raccourcit la séquence de $(K-1)d$ pas, soit de $d$ pas dans WaveNet où $K=2$. L'addition avec $\mathbf{x}$ n'est donc pas possible telle quelle : on tronque $\mathbf{x}$ à ses $T-d$ derniers pas, ou on complète l'entrée par $d$ zéros à gauche, ce qui correspond au [[Padding, stride et dilation|padding causal]] de la [[Convolution causale]].
- La convolution $1\times1$ qui suit la porte rétablit le nombre de canaux avant l'addition ; sans elle, les formes des deux termes de la somme différeraient.
- L'unité de WaveNet est une variante à porte de la [[Connexions résiduelles|connexion résiduelle]] : le raccourci et l'addition sont ceux d'un bloc résiduel ordinaire, mais la transformation apprise passe par le produit d'une $\tanh$ et d'une sigmoïde au lieu d'une activation simple.

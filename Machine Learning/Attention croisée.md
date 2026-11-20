#ml-3

# Définition

Une **attention croisée** est une couche d'attention dont les requêtes $Q$ proviennent du décodeur et dont les clés $K$ et les valeurs $V$ proviennent de l'encodeur.

# Modèle

Un encodeur-décodeur de type [[T5 et l'apprentissage multi-tâche|T5]] empile deux piles de blocs, un décodeur seul de type GPT une seule.

Pile de l'encodeur, répétée $N$ fois :

- Multi-Head Attention ;
- Add & Norm ;
- Feed Forward ;
- Add & Norm.

Pile du décodeur T5, répétée $N$ fois :

- Masked Multi-Head Attention ;
- Add & Norm ;
- Multi-Head Attention croisée ;
- Add & Norm ;
- Feed Forward ;
- Add & Norm.

Les entrées traversent une couche de plongement additionnée à un encodage positionnel avant la première pile, et la sortie du décodeur passe par une couche Linear puis un softmax qui fournit les probabilités sur le vocabulaire. Les sorties sont décalées d'un cran vers la droite à l'entrée du décodeur.

Le GPT reprend la pile du décodeur sans la couche croisée : Masked Multi-Head Attention, Add & Norm, Feed Forward, Add & Norm, puis Linear et softmax.

# Propriétés

Le nombre d'attentions sépare nettement les deux familles.

Un T5 en compte trois :

- self-attention de l'encodeur, non masquée ;
- self-attention du décodeur, masquée ;
- attention croisée du décodeur.

Un GPT n'en compte qu'une, la self-attention masquée du décodeur.

| Couche | T5 (encodeur-décodeur) | GPT (décodeur seul) |
|---|---|---|
| Self-attention de l'encodeur | oui, non masquée | non |
| Self-attention masquée du décodeur | oui | oui |
| Attention croisée | oui | non |

La première et la deuxième sont des [[Self-attention|self-attentions]], où requêtes, clés et valeurs sortent d'une même séquence ; seule la troisième fait dialoguer deux séquences. C'est elle qui manque au GPT, et c'est pourquoi un décodeur seul ne dispose pas d'un encodage préalable à interroger.

# Interprétation

L'attention croisée est l'attention de l'[[Encodeur-décodeur|encodeur-décodeur récurrent]] : la requête est l'état courant du décodeur $d_i$, les clés et les valeurs sont les états de l'encodeur $h_i$, soit $Q = d_i$ et $K = V = h_i$.

Le décodeur interroge donc une séquence qu'il ne produit pas lui-même : à chaque pas, il décide combien d'attention porter à chaque état de l'encodeur, comme le décodeur récurrent choisissait les $h_i$ à partir de son état $d_t$. Les deux premières attentions, elles, ne regardent que la séquence en cours de traitement.

# Remarque

Le décompte annoncé pour T5 est bien de trois attentions. Une énumération intermédiaire n'en détaille que deux, la self-attention de l'encodeur et celle du décodeur ; l'attention croisée, qui complète l'ensemble, est présentée juste après. Le tableau ci-dessus rétablit les trois.

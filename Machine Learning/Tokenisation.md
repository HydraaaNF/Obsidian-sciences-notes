#ml-3

# Définition

La **tokenisation** est l'opération qui convertit un texte en nombres : c'est le travail du **tokenizer** (tokeniseur), première étape du traitement d'un texte par un [[Architecture du Transformer|Transformer]].

Le tokenizer découpe le texte en jetons (*tokens*) et remplace chaque jeton par un entier, son **identifiant de jeton** (*token id*), lu dans un **vocabulaire**. Le vocabulaire est donc un dictionnaire qui associe un identifiant entier à chaque unité de texte.

Le vocabulaire est construit de façon à pouvoir représenter **tout mot possible**, y compris un mot jamais rencontré à l'entraînement : il ne se limite pas aux mots entiers mais contient des fragments plus petits, les sous-mots, dont la concaténation reconstitue un mot inconnu. Plusieurs algorithmes de tokenisation existent ; le plus utilisé est **BPE** (*Byte Pair Encoding*).

# Modèle

Le trajet d'un texte jusqu'au modèle se décompose en trois temps :

- le texte brut est découpé en jetons ;
- chaque jeton est remplacé par son identifiant entier, tiré du vocabulaire du tokenizer ;
- la suite d'identifiants est transmise à la couche qui la convertit en vecteurs, voir [[Couche de plongement]], à l'entrée de l'[[Architecture du Transformer]].

Le vocabulaire réserve quelques identifiants à des rôles particuliers, indépendants du contenu :

| Identifiant | Rôle |
|---|---|
| 0 | début de séquence |
| 1 | remplissage (*padding*) |
| 2 | fin de séquence |

Les identifiants de contenu occupent les valeurs restantes : leur nombre maximal fixe la taille du vocabulaire, et donc le nombre de lignes de la table de plongement qui les reçoit.

Un lot de séquences de longueurs différentes est ramené à une forme rectangulaire par remplissage, voir [[Longueur variable des séquences]] : les séquences courtes reçoivent des jetons de remplissage jusqu'à la longueur de la plus longue.

# Exemple

```python
inputs = tokenizer(["My cat is ugly", "Hello, my dog is cute."],
                   return_tensors="pt", padding=True, padding_side='left')
print(inputs['input_ids'])
```

```text
tensor([[    1,     1,     0,  2646,  7515,    83,    75, 110608,     2],
        [    0, 35378,     4,   759, 10269,    83,  99942,      5,     2]])
```

Les deux phrases n'ont pas la même longueur : la première produit cinq jetons de contenu, soit sept identifiants hors remplissage (début et fin compris), la seconde sept jetons de contenu, soit neuf identifiants. Le remplissage complète la plus courte avec deux `1` sur la gauche, si bien que les deux lignes comptent neuf positions et que le dernier jeton de chaque ligne reste aligné à droite.

Chaque entier est un identifiant du vocabulaire du tokenizer ; la sortie est un `torch.Tensor` de forme `(batch_size, sequence_length)`, ici `(2, 9)`.

# Propriétés

- La sortie du tokenizer est un tenseur d'entiers de forme `(batch_size, sequence_length)` : la longueur de séquence est celle du lot, remplissage compris.
- Les identifiants `0`, `1` et `2` sont réservés au début de séquence, au remplissage et à la fin de séquence ; ils ne portent aucun contenu lexical.
- Le remplissage à gauche (`padding_side='left'`) place les jetons de remplissage en tête de ligne, ce qui laisse la fin de chaque séquence alignée à droite.
- La tokenisation est indépendante du modèle : elle produit des identifiants, que la [[Couche de plongement]] transforme ensuite en vecteurs.

# Remarque

Deux textes passés au même tokenizer donnent des identifiants comparables ; un vocabulaire différent rend les identifiants incomparables, puisque la correspondance entre un jeton et son entier est propre au vocabulaire construit.

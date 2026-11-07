#ml-1

# Définition

En classification, la sortie attendue est un **symbole** : une classe, ou étiquette, prise dans un ensemble fini de $K$ classes.

Un réseau de neurones ne produit pas de symboles, seulement des nombres. Il fournit donc :

- une **probabilité par classe**, c'est-à-dire une régression sur $K$ nombres ;
- puis une **décision**, qui retient $0$, $1$ ou plusieurs classes.

La classification est l'un des trois problèmes de l'[[Problèmes d'apprentissage statistique|apprentissage statistique]], avec la régression et l'estimation de densité.

Selon ce que l'on autorise à la sortie et la règle de décision appliquée, on distingue trois types de classification :

| Type | Sorties | Décision | Réponses possibles |
| --- | --- | --- | --- |
| Binaire | $1$, $\mathbb{P}(\text{chien})$ | $\geq 0.5$ | chien, ou chat |
| Multi-classe | $K$, de somme $1$ | $\arg\max$ | une seule parmi chat, chien, oiseau |
| Multi-étiquette | $K$, chacune dans $(0, 1)$ | chacune $\geq 0.5$ | $\{$chat, chien$\}$, $\{\}$, etc. |

# Interprétation

La décision transforme un vecteur de $K$ probabilités en $0$, $1$ ou plusieurs symboles ; c'est elle qui distingue les trois types.

**Binaire.** Une seule sortie suffit, la probabilité de l'une des deux classes, et le seuil $0.5$ renvoie l'exemple à l'une ou à l'autre. C'est le cadre de la [[Classification binaire]] et de la [[Régression logistique]].

**Multi-classe.** Une seule réponse est attendue, donc les classes **se concurrencent** ; la décision retient la plus probable :

$$c^* = \arg\max_c \mathbb{P}(c \mid x)$$

**Multi-étiquette.** Plusieurs réponses sont possibles à la fois, une photo peut montrer un chat **et** un chien, ou aucun animal, donc les classes sont **indépendantes** ; la décision retient chaque classe dont la probabilité dépasse le seuil :

$$\{ c \mid \mathbb{P}(c \mid x) \geq 0.5 \}$$

# Exemple

Une photo, et $K = 3$ classes : chat, chien et oiseau.

Le classifieur renvoie un nombre par classe, la décision un symbole :

| Classe | Probabilité |
| --- | --- |
| chat | $0.24$ |
| chien | $0.66$ |
| oiseau | $0.10$ |

Le flux complet va des $n$ valeurs d'entrée aux $K$ valeurs de sortie, puis aux $0$, $1$ ou plusieurs classes retenues :

- photo $x$ → classifieur → $\mathbb{P}(\text{chat}) = 0.24$, $\mathbb{P}(\text{chien}) = 0.66$, $\mathbb{P}(\text{oiseau}) = 0.10$ ;
- puis décision → chien.

# Propriétés

La dernière couche, la perte et la décision se déduisent du type de classification :

| Type | Sorties | Activation | Perte | Décision |
| --- | --- | --- | --- | --- |
| Binaire | $1$ | sigmoïde | BCE | $\hat{y} \geq 0.5$ |
| Multi-étiquette | $K$ | $K$ sigmoïdes | BCE moyennée | chaque $\hat{y}_c \geq 0.5$ |
| Multi-classe | $K$ | [[Fonction softmax|softmax]] | CE | $\arg\max_c \hat{y}_c$ |

- BCE désigne l'entropie croisée binaire ([[Entropie croisée binaire]]) ; CE l'entropie croisée ([[Entropie croisée multi-classe]]).
- Le domaine de $y$ fixe la dernière activation : c'est la règle de la première et de la dernière couche.

# Remarque

- La [[Classification binaire]] est le cas à deux classes des deux autres types : une seule sigmoïde à la place de $K$ sigmoïdes, ou un [[Fonction softmax|softmax]] sur deux scores.
- La [[Classification multi-étiquette]] est $K$ classifications binaires côte à côte.
- Deux questions pour situer un problème : étiqueter une photo avec tous les animaux qu'elle montre, à quelle ligne du tableau correspond-elle ? Prédire la lettre suivante d'un nom, à quelle ligne, et que vaut $K$ ?

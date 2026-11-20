#ml-3

# Définition

BERT est un modèle de langage masqué bâti sur la variante encodeur seul du [[Variantes du Transformer|Transformer]]. Il prédit les jetons masqués d'une séquence à partir du contexte situé à leur gauche et à leur droite : l'attention n'est pas masquée, chaque position accède à l'ensemble de la séquence. Aucune étiquette n'est nécessaire, n'importe quel texte fournit les couples entrée-cible, ce qui range cet entraînement parmi les pré-entraînements.

# Modèle

## Chaîne de calcul

- entrée : les jetons `the`, `little`, `[MASK]`, `sleeps`
- chaque jeton est projeté par une couche de plongement additionnée d'un [[Encodage positionnel|encodage positionnel]]
- le `Transformer encoder` applique une attention non masquée : chaque position voit toute la séquence, à gauche comme à droite
- une tête de sortie `Linear + softmax over the vocabulary` est appliquée à chaque position
- les sorties sont $o_1, o_2, o_3, o_4$
- la position masquée produit la prédiction `cat`
- la perte n'est calculée que sur les jetons masqués

| Étape | Rôle |
|---|---|
| Jetons | `the`, `little`, `[MASK]`, `sleeps` |
| Plongement et encodage positionnel | représentation vectorielle du jeton, contextualisée par sa position |
| `Transformer encoder` | attention bidirectionnelle, non causale |
| `Linear + softmax` | distribution sur le vocabulaire à chaque position |
| Sorties | $o_1, o_2, o_3, o_4$ |
| Prédiction | $\hat{y}_3 = \mathrm{cat}$ |

L'absence de masque distingue ce modèle de l'attention causale décrite dans [[Masque causal]] : rien n'interdit à une position de lire celles qui la suivent.

## Perte du modèle de langage masqué

$$
\mathcal{L} = -\sum_{i \in \mathcal{M}} \log \mathbb{P}\left(w_i \mid \tilde{w}\right)
$$

- $\mathcal{M}$ : ensemble des positions masquées
- $\tilde{w}$ : séquence corrompue, où ces positions portent le jeton `[MASK]`
- $w_i$ : jeton d'origine à la position $i$
- $\mathbb{P}\left(w_i \mid \tilde{w}\right)$ : probabilité que le modèle assigne à ce jeton, lue dans le softmax de la position $i$

Seules les positions masquées contribuent à la perte ; les sorties des positions intactes sont ignorées. Chaque terme est l'entropie croisée entre la distribution prédite et le jeton caché, au sens de [[Entropie croisée multi-classe]] : une somme de $-\log$ des probabilités attachées aux bons jetons.

# Exemple

| Position | 1 | 2 | 3 | 4 |
|---|---|---|---|---|
| Texte d'origine | `the` | `little` | `cat` | `sleeps` |
| Entrée corrompue | `the` | `little` | `[MASK]` | `sleeps` |

La position masquée est la troisième, donc $\mathcal{M} = \{3\}$. L'encodeur lit les quatre jetons, la tête de sortie transforme $o_3$ en distribution sur le vocabulaire, et le jeton de probabilité maximale est `cat`.

$$
\hat{y}_3 = \mathrm{cat}
$$

La perte se réduit alors au seul terme de cette position :

$$
\mathcal{L} = -\log \mathbb{P}\left(\mathrm{cat} \mid \tilde{w}\right)
$$

Les sorties $o_1$, $o_2$ et $o_4$ ne sont pas supervisées : le texte d'origine fournit la cible sans aucune annotation humaine.

# Propriétés

- **non causal** : chaque position accède à toute la séquence, avant comme après elle
- **non autorégressif** : le modèle ne produit pas la séquence un jeton après l'autre en réinjectant ses sorties
- **non destiné à la génération libre** : il remplit des trous, il n'engendre pas un texte continu
- **petit** : environ 340 M de paramètres pour le plus grand des BERT

Le caractère non génératif demande une nuance : le modèle de langage masqué produit bien, à chaque position masquée, une distribution sur le vocabulaire, et c'est cette distribution qui donne `cat`. Il peut donc compléter un jeton masqué, mais il ne fait pas ce que fait un décodeur seul entraîné à prédire le jeton suivant, voir [[Transformer décodeur seul]].

# Interprétation

Le pré-entraînement ne vise aucune tâche particulière : le texte brut suffit à fabriquer des cibles en masquant des jetons au hasard. Ce qui est appris est une représentation bidirectionnelle de chaque position, réutilisable ensuite pour des tâches de comparaison de phrases, voir [[Plongements de phrases avec SBERT]].

# Remarque

La taille du plus grand BERT est de l'ordre de 340 M de paramètres ; l'ordre de grandeur de 500 M surestime ce modèle.

L'énoncé « non destiné à la génération » vaut pour la génération libre de texte : le modèle produit néanmoins une distribution sur le vocabulaire aux positions masquées, ce qui permet de compléter un trou.

Dans l'exemple, la prédiction `cat` est celle de la position masquée, la troisième, donc celle de la sortie $o_3$ ; détacher la prédiction de cet indice rendrait la correspondance ambiguë.

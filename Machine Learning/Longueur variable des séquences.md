#ml-1

# Modèle

Un réseau feed-forward, voir [[Perceptron multicouche]], applique une fonction $f$ à une entrée de dimension fixée : il ne reçoit pas directement une [[Données séquentielles|séquence]] de longueur variable. Deux options ramènent l'entrée à une taille fixe.

**Fenêtre** sur les $N$ derniers éléments :

$$\hat{y}_t = f(x_{t-N+1}, \ldots, x_t)$$

- prédire la lettre suivante à partir des 4 précédentes, ou le mois suivant à partir des $W$ précédents ;
- tout ce qui est plus ancien que $N$ pas est invisible.

**Séquence entière** en une fois, de longueur fixée $T$ :

$$(\hat{y}_1, \ldots, \hat{y}_T) = f(x_1, \ldots, x_T)$$

- les séquences plus longues que $T$ sont tronquées, les plus courtes sont complétées.

Dans les deux cas, chaque position a ses propres poids : le mot « chat » en position 2 et le même mot en position 5 sont appris séparément.

La longueur est donc fixée à l'avance, et rien n'est partagé entre les positions.

# Définition

Pour une longueur cible $T$ :

- **troncature** : ne garder que $T$ éléments d'une séquence trop longue, au début ou à la fin ;
- **remplissage** (padding) : ajouter à une séquence trop courte des symboles de remplissage, souvent $0$, jusqu'à la longueur $T$ ;
- le symbole de remplissage est un symbole spécial, qui ne doit pas être confondu avec une valeur réelle.

# Exemple

Avec $T = 5$, la séquence `[a b c d e f g]` est tronquée en `[a b c d e]` ou en `[c d e f g]` : l'information au-delà de $T$ éléments est perdue.

Toujours avec $T = 5$, la séquence `[a b c]` est complétée en `[a b c 0 0]` ou en `[0 0 a b c]`.

Trois noms de longueurs différentes, `lecorve`, `li` et `martin`, réunis dans un même lot par remplissage à droite à la longueur 7, donnent :

- `lecorve` ;
- `li00000` ;
- `martin0`.

Le masque associé vaut 1 sur les pas réels et 0 sur le remplissage :

| séquence | masque |
| --- | --- |
| $x_1$ `lecorve` | `1111111` |
| $x_2$ `li00000` | `1100000` |
| $x_3$ `martin0` | `1111110` |

# Algorithme

Un lot est un tenseur unique : toutes les séquences d'un lot doivent donc avoir la même longueur. On les complète jusqu'à la plus longue, voir [[Lots, époques et chargement des données]] pour le découpage en lots.

`pad_sequence` effectue ce remplissage, par des zéros placés après la fin de chaque séquence :

```python
from torch.nn.utils.rnn import pad_sequence

seqs = [torch.randn(7, n), torch.randn(2, n),
        torch.randn(6, n)]
batch = pad_sequence(seqs, batch_first=True)
batch.shape  # (3, 7, n): zeros after the end
```

Avec un `DataLoader`, on passe un `collate_fn` qui appelle `pad_sequence`.

Comme $0$ peut être une valeur réelle, le remplissage ne doit pas compter dans la perte, une [[Entropie croisée multi-classe|entropie croisée multi-classe]] : on conserve un **masque**, égal à 1 pour un pas réel et à 0 pour un pas de remplissage, et l'on moyenne la perte sur les seuls pas réels.

```python
# logits: (B, T, K), targets: (B, T), lengths: (B,)
mask = (torch.arange(T) < lengths[:, None]).float()
ce = nn.CrossEntropyLoss(reduction='none')
l = ce(logits.flatten(0, 1), targets.flatten())
loss = (l * mask.flatten()).sum() / mask.sum()
```

La même chose s'obtient en réservant une classe au remplissage : `nn.CrossEntropyLoss(ignore_index=PAD)`.

Dans un réseau récurrent, `pack_padded_sequence` arrête chaque séquence à sa vraie longueur, si bien que $h_T$ est son véritable dernier état.

# Remarque

La troncature jette de l'information ; le remplissage n'en jette pas, mais introduit des valeurs qui n'en sont pas.

Le remplissage peut se faire à gauche plutôt qu'à droite : pour générer des noms de longueur variable, on complète à gauche afin que les premières lettres disposent elles aussi de quatre lettres de contexte.

Le remplissage revient avec les [[Réseau récurrent|réseaux récurrents]], pour réunir dans un même lot des séquences de longueurs différentes.

Dans les deux options de longueur fixe, les poids sont propres à chaque position : un motif appris en position 2 n'est pas réutilisé en position 5.

Le remplissage et le masque précèdent toute lecture d'un lot de séquences de longueurs différentes, quelle que soit la sortie visée, voir [[Encodage d'une séquence]].

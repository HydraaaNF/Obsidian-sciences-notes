#ml-3

# Définition

Le **cache de clés et de valeurs** est la mémoire, tenue pendant l'inférence d'un décodeur, des clés $k_j$ et des valeurs $v_j$ déjà calculées pour les tokens traités. À chaque nouveau token, seuls $q_t$, $k_t$ et $v_t$ sont calculés, puis $q_t$ est comparé aux clés des tokens passés, relues au cache, et à $k_t$.

Le cache repose sur une invariance créée par le [[Masque causal]] : dans la [[Self-attention]], la clé $k_j$ et la valeur $v_j$ sont les projections du seul token $j$. Aucun token ultérieur n'entre dans leur calcul, donc les clés et les valeurs des tokens passés **ne changent jamais** une fois obtenues. Seules les projections du nouveau token sont à calculer, celles des tokens passés étant relues au cache.

# Modèle

On note $d_{\text{emb}}$ la dimension de plongement et $d_k$ la dimension des clés. Au pas $t$, la requête est une seule ligne $q_t$, les clés forment la matrice $K_{1:t}$ dont les lignes sont $k_1, \dots, k_t$, et les valeurs la matrice $V_{1:t}$ de lignes $v_1, \dots, v_t$. La ligne $t$ du masque est nulle sur les positions $1, \dots, t$, si bien que le softmax porte sur les $t$ clés :

$$
\operatorname{softmax}\left(\frac{q_t K_{1:t}^\top}{\sqrt{d_k}}\right) V_{1:t}
$$

Le produit $q_t K_{1:t}^\top$ fournit $t$ scores, la division par $\sqrt{d_k}$ les ramène à une échelle stable, le softmax les transforme en poids positifs de somme $1$, et la multiplication par $V_{1:t}$ forme la moyenne pondérée des valeurs :

$$
v'_t = \sum_{j=1}^{t} \alpha_{t,j} v_j
$$

Les formes suivent la lecture du cache. La requête vaut $(1, d_{\text{emb}})$, la transposée des clés $(d_k, t)$ avec $d_k = d_{\text{emb}}$, les scores $(1, t)$, les valeurs $(t, d_{\text{emb}})$ et la sortie $(1, d_{\text{emb}})$. Les projections $k_t$ et $v_t$ du token courant sont calculées au pas courant puis jointes aux clés et valeurs lues au cache : $K_{1:t}$ et $V_{1:t}$ contiennent les tokens $1, \dots, t$, pas seulement les tokens passés.

# Algorithme

Génération du token $t$, le cache contenant déjà les couples $(k_1, v_1), \dots, (k_{t-1}, v_{t-1})$ :

1. Calculer $q_t$, $k_t$ et $v_t$ pour le nouveau token seulement.
2. Lire au cache les $t-1$ clés et valeurs déjà rangées, et former $K_{1:t}$ et $V_{1:t}$ avec le couple courant.
3. Calculer les scores $q_t K_{1:t}^\top$, les diviser par $\sqrt{d_k}$, appliquer le softmax sur les $t$ positions.
4. Multiplier les poids par $V_{1:t}$ pour obtenir $v'_t$, puis ranger $k_t$ et $v_t$ dans le cache pour le pas suivant.

Le déroulé sur les premiers tokens montre la lecture effective du cache. À l'étape 1, le cache est vide : le token 1 se lit lui-même. À l'étape 2, la clé $k_1$ et la valeur $v_1$ sont lues au cache et ne sont pas recalculées ; le produit $QK^\top$ a la forme $(1, 2)$ au lieu de $(2, 2)$. À l'étape 3, deux clés et deux valeurs viennent du cache et les scores valent $(1, 3)$. À l'étape 4, seuls $q_4$, $k_4$ et $v_4$ sont neufs, et les scores valent $(1, 4)$.

| Étape | $Q$ | $K_{1:t}^\top$ | $QK^\top$ | $V_{1:t}$ | Sortie |
| --- | --- | --- | --- | --- | --- |
| 1 | $(1, d_{\text{emb}})$ | $(d_k, 1)$ | $(1, 1)$ | $(1, d_{\text{emb}})$ | $(1, d_{\text{emb}})$ |
| 2 | $(1, d_{\text{emb}})$ | $(d_k, 2)$ | $(1, 2)$ | $(2, d_{\text{emb}})$ | $(1, d_{\text{emb}})$ |
| 3 | $(1, d_{\text{emb}})$ | $(d_k, 3)$ | $(1, 3)$ | $(3, d_{\text{emb}})$ | $(1, d_{\text{emb}})$ |
| 4 | $(1, d_{\text{emb}})$ | $(d_k, 4)$ | $(1, 4)$ | $(4, d_{\text{emb}})$ | $(1, d_{\text{emb}})$ |

Sans cache, les mêmes étapes recalculent toutes les lignes et le produit des scores garde la taille du préfixe entier :

| Étape | $QK^\top$ sans cache | $QK^\top$ avec cache |
| --- | --- | --- |
| 1 | $(1, 1)$ | $(1, 1)$ |
| 2 | $(2, 2)$ | $(1, 2)$ |
| 3 | $(3, 3)$ | $(1, 3)$ |
| 4 | $(4, 4)$ | $(1, 4)$ |

À l'étape 4 sans cache, la matrice des scores est de forme $(4, 4)$ et triangulaire après masquage, les positions futures valant $-\infty$ avant le softmax. Avec cache, la même étape n'évalue que la dernière ligne, de forme $(1, 4)$, qui ne contient aucune position future.

# Exemple

Un décodeur de type GPT-2 reçoit l'amorce `recite the first law $` et doit produire la suite `A robot may not`. Les tokens sont ajoutés un par un à l'entrée, et le modèle est relancé à chaque fois.

| Position | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Entrée | recite | the | first | law | `$` | A | robot | may |
| Sortie | A | robot | may | not | | | | |

La première passe porte sur cinq tokens : la matrice des scores est de forme $(5, 5)$, mais seule sa dernière ligne sert à prédire `A`. La deuxième passe reprend les six tokens et recalcule les clés et valeurs des cinq premiers, pour ne lire encore que le dernier rang. Quatre tokens générés coûtent ainsi quatre passes, dont trois recalculent des clés et des valeurs déjà connues.

Avec le cache, l'amorce de cinq tokens se traite en une passe unique, puis chaque token ajouté ne calcule que son triplet $(q_t, k_t, v_t)$ et lit le reste en mémoire. Les scores d'un token nouveau gardent la forme $(1, t)$, celle du premier token traité seul valant $(1, 1)$ ; la sortie du dernier rang est obtenue sans refaire les projections du préfixe.

# Propriétés

Le gain par pas porte sur la forme du produit des scores : elle passe de $(n, n)$ pour un préfixe de $n$ tokens à $(1, n)$ pour le nouveau token, et les projections des $t-1$ tokens déjà traités ne sont plus refaites. Sur $1\,000$ tokens, le gain de vitesse mesuré atteint un facteur d'environ $5$.

Le résultat est identique à celui du calcul sans cache : les mêmes clés, les mêmes valeurs et les mêmes scores sont combinés, seul le travail déjà fait est conservé. Le cache est une mémoïsation, pas une approximation.

Le coût par token devient linéaire en la longueur du contexte, puisque le nouveau token compare sa requête aux $t$ clés gardées. Le coût total d'une génération de $n$ tokens reste quadratique en $n$, chaque pas parcourant un préfixe plus long.

Le cache croît avec le contexte. Il garde deux tenseurs, les clés et les valeurs, pour chaque token déjà traité et pour chaque couche du modèle, si bien que sa taille augmente à chaque pas et n'est bornée que par la longueur maximale admise. Une génération longue échange ainsi du calcul contre de la mémoire.

# Interprétation

Le cache exploite une asymétrie entre l'entraînement et l'inférence. À l'entraînement, le [[Masque causal]] autorise le traitement de toute la séquence en une passe, chaque position lisant son passé dans la même matrice. À l'inférence, la séquence s'allonge d'un token à la fois et le modèle ne connaît pas encore la suite : le calcul redevient séquentiel, comme dans toute [[Génération d'une séquence]].

Sans cache, l'inférence traite à chaque pas toute la séquence d'entrée. Seul le dernier rang de la sortie est utile, puisque les rangs précédents correspondent à des tokens déjà produits, mais les $K$ et $V$ de tous les tokens précédents sont recalculés. Comme le montre l'[[Inférence autorégressive]] pour un modèle autorégressif quelconque, la réponse n'étant pas connue d'avance, générer $n$ tokens demande $n$ passes. Chaque pas repaie ainsi le traitement du préfixe entier alors que la sortie utile tient en une ligne. Le cache supprime ce travail redondant en s'appuyant sur le fait que le passé est figé : une clé déjà calculée reste valable pour tous les tokens suivants. Le gain grandit avec la longueur du contexte, ce qui rend la génération de textes longs praticable.

Le cache et l'efficacité du noyau d'attention sont deux leviers distincts. Le cache évite de recalculer les clés et les valeurs, tandis qu'une implémentation comme [[FlashAttention]] réduit le trafic mémoire du calcul d'attention lui-même, sans changer les tenseurs échangés.

# Remarque

Un schéma simplifié du calcul peut montrer directement le produit des scores multiplié par les valeurs. La version retenue ici rétablit la division par $\sqrt{d_k}$ et le softmax : sans eux, le produit n'est plus une moyenne pondérée des valeurs et les scores ne sont pas des poids.

L'étiquette « clés des tokens passés » posée sur la transposée des clés est trop étroite. La matrice inclut la clé du token courant, sans laquelle ce token ne pourrait pas se lire lui-même, et sa largeur vaut $t$, nombre de tokens lus, token courant compris.

Un panneau « avec cache » qui répète le contenu de la première étape ne montre aucune lecture. Le cache ne devient visible que si une case est explicitement lue, par exemple la clé $k_1$ réutilisée au token 2, ou si la forme des scores passe de $(2, 2)$ à $(1, 2)$.

La progression des étapes est ici numérotée de $1$ à $4$. Une numérotation qui commence à l'étape 2 laisse croire qu'une étape a été omise, alors que la première étape est celle du token initial, où le cache est encore vide.

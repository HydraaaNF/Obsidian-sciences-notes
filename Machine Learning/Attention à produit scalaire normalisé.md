#ml-3

# Définition

L'**attention à produit scalaire normalisé** calcule une sortie contextualisée à partir de trois matrices $Q$, $K$ et $V$, par des produits scalaires entre requêtes et clés, mis à l'échelle puis normalisés par un softmax.

$$V' = \operatorname{softmax}\left(\frac{QK^{\top}}{\sqrt{d_k}}\right)V$$

La dimension $d_k$ est celle des clés, donc celle des vecteurs $q_i$ et $k_j$ dont le produit scalaire forme les scores.

# Modèle

Le calcul d'une tête se déroule en trois temps.

Les **scores** rassemblent tous les produits scalaires $q_i \cdot k_j$ d'un coup, ce qui impose de transposer $K$.

$$Z = \frac{Q K^{\top}}{\sqrt{d_k}}$$

$$Z_{ij} = \frac{q_i \cdot k_j}{\sqrt{d_k}}$$

Les **poids** appliquent la [[Fonction softmax]] sur chaque ligne de $Z$, si bien que chaque ligne somme à un.

$$A = \operatorname{softmax}(Z)$$

$$\sum_j a_{ij} = 1$$

Le **résultat** est la somme pondérée des valeurs.

$$V' = AV$$

$$v'_i = \sum_j a_{ij} v_j$$

La couche empile ces opérations de bas en haut.

- `MatMul` sur $Q$ et $K$ ;
- `Scale` ;
- `Mask` (optionnel) ;
- `SoftMax` ;
- `MatMul` avec $V$.

Le masquage ajoute aux scores une matrice $M$ composée de 0 et de $-\infty$ avant le softmax.

$$V' = \operatorname{softmax}\left(\frac{QK^{\top}}{\sqrt{d_k}} + M\right)V$$

Dans un décodeur, $Q$, $K$ et $V$ sont les projections d'une même séquence $T$, avec $Q = T W_Q$, $K = T W_K$ et $V = T W_V$ : c'est la [[Self-attention]], et le masque $M$ la rend causale, voir [[Masque causal]].

# Propriétés

$q_i \cdot k_j$ est un produit scalaire, donc une vraie similarité entre la requête $i$ et la clé $j$ : plus les deux vecteurs pointent dans la même direction, plus le score est élevé.

La division par $\sqrt{d_k}$ n'est pas décorative. Les produits scalaires croissent avec $d_k$, et sans remise à l'échelle les scores deviendraient assez grands pour saturer le softmax, qui ne renverrait plus qu'un poids quasi nul ou quasi unitaire.

Les formes se déduisent de la règle du produit matriciel ([[Forme d'un tenseur]]). Pour une tête sur quatre tokens de dimension 128, $Q, K, V \in \mathbb{R}^{4 \times 128}$, le softmax et la division par $\sqrt{d_k}$ ne changeant aucune forme.

$$Q\,[4,128] \times K^{\top}\,[128,4] = Z\,[4,4]$$

$$A\,[4,4] \times V\,[4,128] = V'\,[4,128]$$

$Z$ contient un score par paire de tokens, requête $i$ et clé $j$ ; $A$, de même forme, un poids par paire ; $V'$ un vecteur par token, exactement comme $V$.

Les têtes d'une [[Attention multi-têtes]] se concatènent : huit têtes de $[4,128]$ donnent $[4,1024]$, la forme de $T$, ce qui ramène à la bonne forme pour la [[Connexions résiduelles|connexion résiduelle]] $T + \operatorname{MHA}(T)$.

# Exemple

Une tête en PyTorch, avec quatre tokens et $d_k = 128$.

```python
import torch
import torch.nn as nn

sftmx = nn.Softmax(dim=-1)
d_k = 128

Q = torch.randn(4, d_k)
K = torch.randn(4, d_k)
V = torch.randn(4, d_k)

K = K.T
print(K.shape)          # torch.Size([128, 4])
Z = torch.matmul(Q, K) / d_k**0.5
print(Z.shape)          # torch.Size([4, 4])
A = sftmx(Z)
print(A.shape)          # torch.Size([4, 4])
V_prime = torch.matmul(A, V)
print(V_prime.shape)    # torch.Size([4, 128])
```

La transposition de $K$ fournit la forme $[128,4]$ attendue par le produit, le softmax porte sur la dernière dimension, donc sur chaque ligne de scores, et la multiplication finale par $V$ restitue la forme des valeurs.

# Remarque

- [[FlashAttention]] est une implémentation efficace de ce calcul d'attention, qui évite de matérialiser la matrice de scores en mémoire.
- Le [[Score d'attention de Bahdanau]] est un score appris, à comparer au score par produit scalaire employé ici.

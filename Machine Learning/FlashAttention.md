#ml-3

# Définition

**FlashAttention** est une implémentation du calcul de l'[[Attention à produit scalaire normalisé]] optimisée pour le débit d'exécution sur GPU. Sa performance se mesure en TFLOP/s pour la passe avant et la passe arrière de l'attention réunies, en fonction de la longueur de séquence.

# Propriétés

Le débit d'une implémentation de référence en PyTorch sature, voire régresse, quand la longueur de séquence augmente.

Les variantes FlashAttention conservent une croissance du débit sur toute la plage mesurée, de 512 à 16k tokens.

FlashAttention-2 est la variante la plus rapide aux longueurs 8k et 16k, dans les quatre configurations testées.

Le gain s'accroît globalement avec la longueur : sur la configuration avec masque causal et dimension de tête 128, le débit de FlashAttention-2 passe de 99 à 189 TFLOP/s entre 512 et 16k tokens, tandis que PyTorch reste entre 23 et 34 TFLOP/s jusqu'à 8k tokens puis échoue par manque de mémoire à 16k.

# Exemple

Le banc d'essai compare, sur une A100 80 GB SXM4, le débit de l'attention en passe avant et passe arrière pour des longueurs de séquence de 512, 1k, 2k, 4k, 8k et 16k tokens. Quatre configurations croisent la présence d'un masque causal et la dimension de tête.

| Panneau | Masque causal | Dimension de tête |
|---|---|---|
| (a) | sans | 64 |
| (b) | sans | 128 |
| (c) | avec | 64 |
| (d) | avec | 128 |

Le panneau (d) rassemble cinq implémentations : PyTorch, FlashAttention, xformers, FlashAttention Triton et FlashAttention-2.

```chart
type: bar
labels: ["512", "1k", "2k", "4k", "8k", "16k"]
series:
  - title: PyTorch
    data: [23, 28, 32, 32, 34, null]
  - title: FlashAttention
    data: [55, 62, 69, 76, 80, 83]
  - title: xformers
    data: [58, 72, 82, 87, 91, 92]
  - title: FlashAttention Triton
    data: [50, 61, 68, 74, 78, 80]
  - title: FlashAttention-2
    data: [99, 133, 155, 173, 182, 189]
```

# Interprétation

À courte séquence, les écarts restent modérés : à 512 tokens, FlashAttention-2 devance PyTorch d'un facteur proche de quatre sur ce panneau.

L'écart se creuse ensuite globalement, jusqu'à un facteur d'environ cinq aux longueurs 4k et 8k, où FlashAttention-2 atteint 173 puis 182 TFLOP/s contre 32 puis 34 pour PyTorch. À 16k tokens, PyTorch ne livre plus de mesure : l'exécution échoue par manque de mémoire (OOM), alors que FlashAttention-2 atteint 189 TFLOP/s.

La saturation de PyTorch signifie que son débit cesse de suivre l'allongement des séquences, alors que les variantes FlashAttention continuent d'en tirer parti.

Parmi les variantes, FlashAttention, xformers et FlashAttention Triton restent proches les unes des autres, tandis que FlashAttention-2 se détache nettement aux longues séquences.

# Remarque

Les débits sont ceux des étiquettes des barres du graphique ci-dessus, en TFLOP/s.

La mesure réunit passe avant et passe arrière : elle porte sur l'entraînement, alors qu'à l'inférence le [[Cache de clés et de valeurs]] évite de recalculer les clés et les valeurs des tokens déjà traités.

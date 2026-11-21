#ml-1

# Modèle

Un **réseau récurrent** (RNN) est un [[Réseau de neurones]] dont le graphe comporte une boucle : il lit une [[Données séquentielles|séquence]] pas à pas en transportant une mémoire d'un pas au suivant. À chaque pas $t$ :

$$(\hat{y}_t, h_t) = f(x_t, h_{t-1})$$

- $x_t$ : l'entrée au pas $t$ ;
- $h_t$ : l'**état caché**, un résumé de $x_1, \dots, x_t$, qui part de $h_0 = 0$ ;
- $\hat{y}_t$ : la sortie prédite au pas $t$.

C'est la même fonction $f$, avec les mêmes poids, qui sert à chaque pas : les poids sont **partagés dans le temps**. Deux conséquences en découlent :

- une longueur quelconque : il suffit de boucler $T$ fois ;
- ce qui est appris à une position vaut à toutes les positions.

L'état caché $h_t$ représente le préfixe $x_1, \dots, x_t$ : c'est un [[Plongement]].

```mermaid
flowchart LR
    h0["h₀"] --> f1["f"] --> h1["h₁"]
    h1 --> f2["f"] --> h2["h₂"]
    h2 --> f3["f"] --> h3["h₃"]
    x1["x₁"] --> f1
    x2["x₂"] --> f2
    x3["x₃"] --> f3
    f1 --> y1["ŷ₁"]
    f2 --> y2["ŷ₂"]
    f3 --> y3["ŷ₃"]
```

# Interprétation

Chaque $h_t$ mêle l'élément nouveau, par exemple un mot, à tout ce qui le précède, et les éléments les plus anciens s'estompent. La sortie $\hat{y}_t$ peut donc s'appuyer sur tout ce qui a été lu jusque-là, ce qui autorise deux usages :

- l'**étiquetage** : on conserve chaque $\hat{y}_t$, une étiquette par mot ;
- la **classification d'une question** : on ne conserve que $\hat{y}_5$.

Sur la question « What time is it ? », chaque $h_t$ intègre le mot lu au pas $t$ aux mots précédents, et seule la sortie du dernier pas sert à classer la question.

# Propriétés

- L'entraînement se fait par rétropropagation sur le réseau déplié, appelée **rétropropagation dans le temps** (BPTT), voir [[Rétropropagation dans le temps]].

# Remarque

- L'[[Encodeur bidirectionnel et causalité|encodeur bidirectionnel]] est la variante du modèle récurrent qui lit la séquence dans les deux sens.
- La [[Longueur variable des séquences]] impose le remplissage pour réunir dans un même lot des séquences de longueurs différentes traitées par le réseau.
- La [[Self-attention]] compare requêtes, clés et valeurs pour pondérer le contexte, là où le réseau récurrent transporte ce contexte dans un état caché.

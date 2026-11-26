#ml-1

# Définition

La mémoire à long et court terme (LSTM) est une cellule récurrente à deux états, là où la [[Cellule d'Elman]] n'en a qu'un :

- $c_t$, la **cellule**, qui porte une mémoire à long terme ;
- $h_t$, l'état à court terme, celui que lit la couche de sortie.

L'état de cellule n'est pas réécrit à travers une tangente hyperbolique : il est mis à jour par une **addition**.

$$c_t = f_t \odot c_{t-1} + i_t \odot \tilde{c}_t$$

$\tilde{c}_t$ est le contenu nouveau, calculé comme dans une cellule d'Elman ; $f_t$ et $i_t$ sont des **portes** comprises entre 0 et 1, appliquées composante par composante (produit terme à terme $\odot$).

Quand $f_t$ est proche de 1 et $i_t$ proche de 0, $c$ est conservé tel quel, et son gradient aussi : la mémoire peut couvrir des centaines de pas.

# Propriétés

Le schéma de la cellule enchaîne le calcul des portes, l'écriture dans la mémoire, puis la lecture de la sortie ; l'entrée est en rouge, la mémoire en vert, les portes en ambre, le contenu en violet et l'état court en bleu.

```mermaid
flowchart LR
    cp["cₜ₋₁"] --> ct["cₜ = fₜ ⊙ cₜ₋₁ + iₜ ⊙ c̃ₜ"]
    inp["[xₜ ; hₜ₋₁]"] --> gf["σ : porte d'oubli fₜ"]
    inp --> gi["σ : porte d'entrée iₜ"]
    inp --> gc["tanh : contenu c̃ₜ"]
    inp --> go["σ : porte de sortie oₜ"]
    gf --> ct
    gi --> ct
    gc --> ct
    ct --> th["tanh(cₜ)"]
    th --> h["hₜ = oₜ ⊙ tanh(cₜ)"]
    go --> h
    classDef entree fill:#f8d7da,stroke:#b02a37,color:#000
    classDef memoire fill:#d8f5d8,stroke:#1e7b34,color:#000
    classDef sortie fill:#dbe5ff,stroke:#2b4c9b,color:#000
    classDef porte fill:#fff3cd,stroke:#997404,color:#000
    classDef contenu fill:#e7e0f5,stroke:#6f42c1,color:#000
    class inp entree
    class cp,ct,th memoire
    class h sortie
    class gf,gi,go porte
    class gc contenu
```

Au pas suivant, $h_t$ devient $h_{t-1}$ et $c_t$ devient $c_{t-1}$ : les deux états sont ceux que la cellule retrouve en entrée.

Chaque porte et le contenu sont calculés par une couche dense appliquée à la concaténation de l'entrée et de l'état précédent, suivie d'une activation :

$$f_t = \sigma(W_f [x_t ; h_{t-1}] + b_f)$$

$$i_t = \sigma(W_i [x_t ; h_{t-1}] + b_i)$$

$$o_t = \sigma(W_o [x_t ; h_{t-1}] + b_o)$$

$$\tilde{c}_t = \tanh(W_c [x_t ; h_{t-1}] + b_c)$$

$$c_t = f_t \odot c_{t-1} + i_t \odot \tilde{c}_t$$

$$h_t = o_t \odot \tanh(c_t)$$

- $f_t$, $i_t$ et $o_t$ passent par une sigmoïde $\sigma$ ;
- $\tilde{c}_t$ passe par une tangente hyperbolique ;
- $c_t$ combine l'ancienne mémoire $c_{t-1}$ et le contenu nouveau $\tilde{c}_t$ par une addition pondérée ;
- $h_t$ est l'état de cellule filtré par la porte de sortie.

La cellule transmet ses deux états au pas suivant, mais n'en expose qu'un : $h_t$ part vers la couche de sortie, tandis que $c_t$ reste interne et ne sert qu'à la récurrence, si bien que rien de la mémoire longue ne va directement à la prédiction.

La porte de sortie $o_t$ n'est pas la couche de sortie : elle dose la part de $\tanh(c_t)$ montrée dans $h_t$, à l'intérieur de la cellule. La prédiction vient d'une couche distincte, à l'extérieur, appliquée à $h_t$ :

$$\hat{y}_t = g(W_y h_t + b_y)$$

$g$ est l'activation choisie selon la tâche, voir [[Première et dernière couches]] ; les mêmes $W_y$ servent à tous les pas. On conserve un $\hat{y}_t$ par pas pour l'étiquetage, ou seulement celui du dernier $h_T$ pour une classification, voir [[Tâches sur les séquences]].

Trois portes, oubli, entrée et sortie : chacune est une régression logistique par composante, c'est-à-dire un [[Neurone artificiel|neurone]]. Quatre couches denses sur $[x_t ; h_{t-1}]$ : quatre fois les poids d'une cellule d'Elman.

# Interprétation

- La sigmoïde, à valeurs dans $(0, 1)$, est un **cadran** pour les portes $f_t$, $i_t$ et $o_t$.
- Le contenu $\tilde{c}_t$ est produit par la [[Fonctions d'activation|tangente hyperbolique]], dont la valeur signée permet d'y écrire $+1$ ou $-1$.
- $\tilde{c}_t$ indique *ce qui* pourrait être écrit ; $i_t$ *quelle quantité* en écrire ; $f_t$ *quelle part* de l'ancienne mémoire garder ; $o_t$ *quelle part* de la mémoire montrer dans $h_t$.

Une dimension de $c$ peut par exemple porter le nombre du sujet : $+1$ pour un singulier, $-1$ pour un pluriel.

- Un nouveau sujet : $f \approx 0$, $i \approx 1$, $\tilde{c} = \pm 1$ : effacer, puis écrire.
- Les mots entre les deux : $f \approx 1$, $i \approx 0$ : garder, et le gradient passe.
- Le verbe : $o \approx 1$ : montrer l'information, pour accorder le verbe.

# Remarque

L'addition qui met à jour $c$ est le même mécanisme que celui des [[Connexions résiduelles]] : elle réserve au gradient un chemin direct, au lieu de le faire traverser une tangente hyperbolique à chaque pas.

La cellule LSTM généralise la [[Cellule d'Elman]] : le contenu nouveau s'y calcule de la même façon, mais des portes dosent ce qui est écrit, conservé et montré, au prix de quatre couches denses au lieu d'une.

C'est cette mémoire additive qui fait tenir l'information sur des centaines de pas, là où le gradient d'une cellule d'Elman tend à [[Disparition et explosion du gradient|disparaître]].

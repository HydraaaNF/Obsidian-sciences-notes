#ml-1

# Définition

Déplié sur $T$ pas, un [[Réseau récurrent]] est un réseau à propagation avant de $T$ couches, dont toutes les couches partagent les mêmes poids $\theta = (\theta_u, \theta_o)$. L'entraînement se fait par [[Rétropropagation]] sur ce réseau déplié : c'est la **rétropropagation dans le temps** (*backpropagation through time*, BPTT).

Le dépliage transforme la récurrence en une chaîne de couches identiques : la passe avant enchaîne les $T$ pas, la passe arrière remonte la chaîne.

# Propriétés

- Un poids utilisé à chaque pas reçoit la **somme** de ses gradients sur tous les pas :

$$\frac{\partial L}{\partial \theta} = \sum_{t=1}^{T} \left.\frac{\partial L}{\partial \theta}\right|_{t}$$

- Le coût vient du séquencement : les $T$ pas s'exécutent l'un après l'autre, en avant puis en arrière.
- Chaque $h_t$ doit être conservé pour la passe arrière.

# Algorithme

La forme de la perte dépend de la tâche, donc du nombre de sorties utilisées.

**Many-to-one.** Une seule perte, sur la dernière sortie :

$$L = \ell(\hat{y}_T, y)$$

- Le gradient remonte depuis $L$ à travers $h_{T-1}, h_{T-2}, \dots$, jusqu'au premier pas.
- Usage : prédire le mois suivant à partir des $W$ mois précédents.

```mermaid
flowchart LR
    subgraph S1["pas 1"]
        x1["x₁"] --> f1["f"]
        h0["h₀"] --> f1
        f1 --> y1["ŷ₁<br/>inutilisée"]
    end
    subgraph S2["pas 2"]
        x2["x₂"] --> f2["f"]
        f2 --> y2["ŷ₂<br/>inutilisée"]
    end
    subgraph S3["pas 3"]
        x3["x₃"] --> f3["f"]
        f3 --> y3["ŷ₃"]
    end
    f1 -->|"h₁"| f2
    f2 -->|"h₂"| f3
    y3 --> loss["ℓ(ŷ₃, y)"]
    loss --> L["L"]
    L -.->|"gradient"| f3
    f3 -.-> f2
    f2 -.-> f1
    classDef entree fill:#f8d7da,stroke:#b02a37,color:#000
    classDef memoire fill:#d8f5d8,stroke:#1e7b34,color:#000
    classDef sortie fill:#dbe5ff,stroke:#2b4c9b,color:#000
    classDef perte fill:#e9ecef,stroke:#495057,color:#000
    classDef calcul fill:#fff3cd,stroke:#997404,color:#000
    class x1,x2,x3 entree
    class h0 memoire
    class f1,f2,f3 calcul
    class y1,y2 perte
    class y3 sortie
    class loss,L perte
```

**Many-to-many.** Une perte par pas, sommée ou moyennée :

$$L = \sum_t \ell(\hat{y}_t, y_t)$$

- Usage : étiquetage, ou prédiction de la lettre suivante à chaque position d'un nom.
- Une séquence très longue, un livre entier par exemple, impose la **BPTT tronquée** : ne rétropropager que sur les $K$ derniers pas, et transporter $h$ vers l'avant sans son gradient (`h.detach()`).

```mermaid
flowchart LR
    x1["x₁"] --> f1["f"]
    h0["h₀"] --> f1
    f1 --> y1["ŷ₁"]
    x2["x₂"] --> f2["f"]
    f1 -->|"h₁"| f2
    f2 --> y2["ŷ₂"]
    x3["x₃"] --> f3["f"]
    f2 -->|"h₂"| f3
    f3 --> y3["ŷ₃"]
    y1 --> l1["ℓ₁"]
    y2 --> l2["ℓ₂"]
    y3 --> l3["ℓ₃"]
    l1 --> s["Σ"]
    l2 --> s
    l3 --> s
    s --> L["L"]
    classDef entree fill:#f8d7da,stroke:#b02a37,color:#000
    classDef memoire fill:#d8f5d8,stroke:#1e7b34,color:#000
    classDef sortie fill:#dbe5ff,stroke:#2b4c9b,color:#000
    classDef perte fill:#e9ecef,stroke:#495057,color:#000
    classDef calcul fill:#fff3cd,stroke:#997404,color:#000
    class x1,x2,x3 entree
    class h0 memoire
    class f1,f2,f3 calcul
    class y1,y2,y3 sortie
    class l1,l2,l3,s,L perte
```

# Remarque

Le gradient d'un poids traverse tous les pas qui l'ont utilisé : plus la séquence est longue, plus la chaîne de multiplications est profonde, ce qui est le mécanisme de la [[Disparition et explosion du gradient]]. La BPTT tronquée coupe cette chaîne en abandonnant le gradient porté par $h$, au prix d'un gradient biaisé.

Chaque pas isolé est décrit dans [[Cellule d'Elman]] ; la récurrence ajoute le passage de l'état au pas suivant.

# Interprétation

La [[Projection linéaire des données|projection linéaire]] $y = Ux$ obtenue par un système propre sert à :

- maximiser la variance des données projetées, avec l'[[Analyse en composantes principales|analyse en composantes principales]] ;
- maximiser la discrimination entre classes, avec l'[[Analyse discriminante linéaire|analyse discriminante linéaire]].

D'autres approches vont au-delà :

- des formes plus complexes de $U$ : la **NMF** (factorisation en matrices non négatives) et l'**ICA** (analyse en composantes indépendantes) ;
- des **transformations non linéaires** : l'emploi de **noyaux** (astuce du noyau, *kernel trick*) et les **réseaux de neurones artificiels** (perceptron multicouche) ;
- les **cartes auto-organisatrices** (*self-organizing maps*).

# Exemple

Un réseau de neurones à couche cachée réduite (un *bottleneck*, ou goulot d'étranglement) réalise une transformation non linéaire :

```mermaid
flowchart LR
    subgraph entree["Couche d'entrée"]
        direction TB
        x1((x₁))
        x2((x₂))
        x3((x₃))
        x4((x₄))
    end
    subgraph cachee["Couche cachée : bottleneck"]
        direction TB
        h1(( ))
        h2(( ))
    end
    subgraph sortie["Couche de sortie"]
        direction TB
        o1((x₁))
        o2((x₂))
        o3((x₃))
        o4((x₄))
    end
    x1 & x2 & x3 & x4 --> h1 & h2
    h1 & h2 --> o1 & o2 & o3 & o4
```

Chaque neurone de la couche d'entrée est relié à chacun des deux neurones de la couche cachée, et chacun de ces deux neurones à chacun des quatre neurones de la couche de sortie.

# Remarque

Pour une autre approche de réduction de dimension, voir l'[[Analyse factorielle]].

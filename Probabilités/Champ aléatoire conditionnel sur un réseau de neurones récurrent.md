# Modèle

Un **champ aléatoire conditionnel sur un réseau de neurones récurrent** empile une couche de [[Champ aléatoire conditionnel à chaîne linéaire|champ aléatoire conditionnel]] sur une couche récurrente de type LSTM. Les observations sont les mots $x_1, \dots, x_n$ d'une phrase, les étiquettes $y = (y_1, \dots, y_n)$ prennent chacune leurs valeurs dans un alphabet fini $\mathcal{Y}$, donc la suite $y$ appartient à $\mathcal{Y}^n$, et $h_1, \dots, h_n$ sont les états cachés produits par le [[Réseau de neurones récurrent|réseau récurrent]] dans le sens de la lecture.

La couche récurrente fournit à chaque position $k$ une probabilité pour chaque étiquette $y_k$ :

$$\mathbb{P}(k, x, y_k) = \operatorname{softmax}(f(x_k, h_k))[y_k]$$

où $f$ est la fonction calculée par le réseau à partir du mot $x_k$ et de l'état caché $h_k$. La couche de champ aléatoire conditionnel ajoute un score de transition $A(y_{k-1}, y_k)$ entre deux étiquettes voisines, et le score d'une suite d'étiquettes devient

$$s(y, x) = \sum_{k=1}^{n} A(y_{k-1}, y_k) + \mathbb{P}(k, x, y_k)$$

La loi conditionnelle du modèle est alors

$$p(y \mid x) = \frac{\exp s(y, x)}{\sum_{y' \in \mathcal{Y}^n} \exp s(y', x)}$$

Sans la couche de champ aléatoire conditionnel, le réseau prédit chaque étiquette indépendamment des autres, à partir du seul état caché de sa position, et le score de la suite s'écrit

$$L(y_1, \dots, y_n) \propto \sum_{k=1}^{n} \operatorname{softmax}(f(x_k, h_k))[y_k]$$

Avec la couche de champ aléatoire conditionnel, le score de la suite s'écrit

$$L(y_1, \dots, y_n) \propto \sum_{k=1}^{n} A(y_{k-1}, y_k) + \mathbb{P}(k, x, y_k)$$

# Exemple

Sur la phrase « EU rejects German call », la couche récurrente lit les mots dans l'ordre et engendre les états cachés $h_1, \dots, h_4$, chacun résumant le préfixe déjà lu. Chaque état caché produit une distribution sur les étiquettes, dont on retient ici l'étiquette la plus probable, en annotation BIO (voir [[Gabarits de traits et annotation BIO]]) : `B-ORG` pour « EU », `O` pour « rejects », `B-MISC` pour « German », `O` pour « call ».

```mermaid
flowchart BT
    subgraph mots["mots"]
        EU["EU"]
        rejects["rejects"]
        German["German"]
        call["call"]
    end
    subgraph reseau["couche récurrente"]
        H1["h₁"]
        H2["h₂"]
        H3["h₃"]
        H4["h₄"]
    end
    subgraph etiquettes["étiquettes"]
        T1["B-ORG"]
        T2["O"]
        T3["B-MISC"]
        T4["O"]
    end
    EU --> H1
    rejects --> H2
    German --> H3
    call --> H4
    H1 --> H2
    H2 --> H3
    H3 --> H4
    H1 --> T1
    H2 --> T2
    H3 --> T3
    H4 --> T4
    T1 --- T2
    T2 --- T3
    T3 --- T4
```

Les flèches verticales portent la prédiction de chaque étiquette à partir de son état caché, la chaîne des états cachés porte la lecture séquentielle des mots, et le trait horizontal qui relie deux étiquettes voisines figure la dépendance ajoutée par la couche de champ aléatoire conditionnel : l'étiquette retenue à une position n'est plus choisie isolément, elle tient compte de ses voisines.

# Interprétation

La couche récurrente calcule pour chaque position une représentation $h_k$ qui résume l'observation, puis la convertit en une distribution sur les étiquettes. La couche de champ aléatoire conditionnel n'ajoute qu'un terme de transition entre étiquettes voisines, que la prédiction directe ne peut pas exprimer puisque chaque étiquette y est prédite séparément (voir [[Prédiction directe par un réseau de neurones récurrent]]).

Le score $s(y, x)$ joue le rôle de la fonction potentielle d'un [[Champ aléatoire conditionnel à chaîne linéaire|champ aléatoire conditionnel]] : il est équivalent à $\sum_i \lambda_i f_i(x, y)$ pour des [[Fonctions de traits pour les séquences|fonctions de traits]] $f_i$ complexes, que le réseau évalue à chaque position par la quantité $f(x_k, h_k)$ et par les scores de transition.

Le dénominateur de $p(y \mid x)$ normalise le score sur les suites d'étiquettes concurrentes : la probabilité d'une suite croît avec son score, et le modèle favorise donc les suites dont les transitions et les étiquettes locales sont bien notées ensemble.

# Algorithme

Le décodage maximise $\ln p(t \mid w)$, où $t$ désigne la suite d'étiquettes et $w$ la suite de mots, en deux étapes :

1. exécuter le réseau récurrent pour obtenir la distribution d'étiquettes $\mathbb{P}(k, :)$ à chaque position $k$ ;
2. appliquer une [[Programmation dynamique pour un champ aléatoire conditionnel|programmation dynamique]] sur ces scores pour trouver la suite d'étiquettes de score maximal.

La rétropropagation suit la même procédure en deux temps : le gradient traverse d'abord la couche de programmation dynamique, puis la couche récurrente, ce qui rend l'ensemble entraînable de bout en bout.

# Remarque

La lettre $L$ désigne deux scores différents dans les deux formules du modèle. Dans la prédiction directe, $L$ agrège les probabilités $\operatorname{softmax}(f(x_k, h_k))[y_k]$ de chaque position, sans aucun couplage entre étiquettes. Dans la couche de champ aléatoire conditionnel, $L$ ajoute à ces mêmes probabilités le terme de transition $A(y_{k-1}, y_k)$, qui couple deux étiquettes voisines. Ce sont deux modèles distincts, et seule la seconde formule décrit un champ aléatoire conditionnel : la présence ou l'absence du terme $A$ indique de laquelle il s'agit.

Le décodage de la suite optimale est celui d'un champ aléatoire conditionnel à chaîne linéaire (voir [[Décodage d'un champ aléatoire conditionnel à chaîne linéaire]]), les scores locaux $A(y_{k-1}, y_k) + \mathbb{P}(k, x, y_k)$ y remplaçant les combinaisons de fonctions de traits.

Dans la loi conditionnelle, la somme du dénominateur porte sur les suites d'étiquettes de longueur $n$ et non sur les étiquettes isolées : $\mathcal{Y}$ est l'alphabet fini des étiquettes, celui qu'indexe $\operatorname{softmax}(\cdot)[y_k]$, et l'espace des suites candidates est $\mathcal{Y}^n$. L'écriture $\sum_{y' \in \mathcal{Y}}$ est une erreur fréquente : elle ne parcourt que les étiquettes simples, alors que la normalisation doit couvrir toutes les suites concurrentes.

# Interprétation

Un échantillon d'un [[Modèles de mélange|modèle de mélange]] est tiré selon la loi de l'une des composantes $f_i()$ du mélange, avec la probabilité $\pi_i$. Concrètement, le tirage d'un échantillon est un processus en deux étapes :

1. choisir une composante $i$ du mélange selon la loi discrète définie par les poids $w_j$ ;
2. tirer un échantillon selon la loi $f_i()$.

Les échantillons d'un modèle de mélange sont donc tirés de l'une des composantes du modèle, dans la proportion définie par les poids : pour chaque composante $i$, il existe un ensemble d'échantillons distribués selon $f_i(x)$, et la proportion de ces échantillons est donnée par $\pi_i$. Il en résulte une variable cachée indiquant la composante à laquelle chaque échantillon appartient.

# Propriétés

La loi de $x$ est la [[Lois marginales|marginale]] sur la variable cachée $Z$ :

$$f(x) = \sum_{i=1}^K \underbrace{\pi_i}_{\mathbb{P}[Z = i]} \underbrace{f_i(x)}_{p(x|Z = i)}$$

Le modèle produit des couples $(Z, X)$ : on tire d'abord la composante $Z$, puis l'observation $X$ selon sa loi conditionnelle. La vraisemblance des observations s'obtient en sommant, sur les valeurs possibles de $Z$, la vraisemblance jointe.

La densité conditionnelle de $x$ sachant $z$ est :

$$p(x\mid z) = f_z(x) = \sum_{i=1}^{K} f_i(x)\,\mathbb{I}_{(z=i)}$$

La densité jointe de $(x, z)$ est :

$$p(x, z) = \pi_z f_z(x) = \left( \sum_{i=1}^K f_i(x) \mathbb{I}_{(z=i)} \right) \left( \sum_{i=1}^K \pi_i \mathbb{I}_{(z=i)} \right)$$

La densité marginale de $x$ est :

$$p(x) = \sum_z p(x, z) = \sum_z \sum_i \pi_i f_i(x) \mathbb{I}_{(z=i)} = \sum_i \pi_i f_i(x)$$

# Remarque

La variable cachée $Z$ fonde l'étape E de l'[[Algorithme d'espérance-maximisation]] ; les densités conditionnelle, jointe et marginale ci-dessus sont réutilisées par l'[[Espérance-maximisation pour un mélange de gaussiennes]]. La loi de $Z$ sachant une observation $x$ s'obtient à partir de ces densités par la [[Formule de Bayes]].

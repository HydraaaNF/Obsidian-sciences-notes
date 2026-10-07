# Définition

Soit $\mathbf{x} = \{x_1, \dots, x_N\}$ un ensemble d'[[Échantillon et échantillonnage|échantillons d'entraînement]] dont on veut estimer les paramètres d'un [[Mélange gaussien|modèle de mélange gaussien]] à $K$ composantes par la [[Méthode du maximum de vraisemblance|méthode du maximum de vraisemblance]], c'est-à-dire

- les poids $\{w_1, \dots, w_K\}$,
- les vecteurs des moyennes $\{\mu_1, \dots, \mu_2\}$,
- les vecteurs des variances $\{\sigma_1, \dots, \sigma_2\}$.

Le critère du maximum de vraisemblance s'écrit

$$\ln f(\mathbf{x}) = \sum_{i=1}^N \ln \left( \sum_{j=1}^K w_j f_j(x_i; \theta_j) \right)$$

# Propriétés

L'ensemble des échantillons d'entraînement $\mathbf{x}$ est **incomplet** ! Supposons que, pour chaque échantillon $x_i$, l'indicateur de composante $z_i$ soit connu : l'ensemble $\{x_1, z_1, \dots, x_N, z_N\}$ est appelé *données complètes*, et les [[Estimateur du maximum de vraisemblance|estimateurs du maximum de vraisemblance]] peuvent être obtenus à partir de ces données, par exemple

$$\hat{w}_i = \frac{1}{N} \sum_{j=1}^N \mathbb{I}_{(z_j=i)}$$

$$\hat{\mu}_i = \frac{\sum_{j=1}^N x_j \mathbb{I}_{(z_j=i)}}{\sum_{j=1}^N \mathbb{I}_{(z_j=i)}}$$

où $\hat{w}_i$ est la proportion d'échantillons attribués à la composante $i$ du [[Modèles de mélange|mélange]] et $\hat{\mu}_i$ la [[Moyenne empirique|moyenne empirique]] de ces échantillons.

Mais les variables $z_j$ ne sont pas connues !

# Remarque

La maximisation directe du critère est (presque) impossible. Résoudre directement les équations du maximum de vraisemblance se heurte en effet à deux difficultés :

- ces équations n'existent souvent pas ;
- lorsqu'elles existent, elles sont complexes.

Un algorithme de descente de gradient présente de plus deux limites :

- la fonction de vraisemblance n'est pas convexe, d'où une non-unicité de la solution ;
- une connaissance a priori du domaine de $\theta$ est nécessaire.

L'[[Algorithme d'espérance-maximisation]] en apporte une solution élégante.

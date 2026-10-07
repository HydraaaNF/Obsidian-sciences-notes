# Définition

L'[[Algorithme d'espérance-maximisation|espérance-maximisation]] estime les paramètres d'un [[Modèles de mélange|mélange]] lorsque l'appartenance des observations aux composantes est inconnue : les poids et les moyennes de chaque composante se calculent alors à partir des espérances des indicatrices d'appartenance.

# Modèle

Pour $N$ observations $\{x_1, \dots, x_N\}$ et une composante $i$, les estimations à appartenance inconnue s'écrivent

$$\hat{w}_i = \frac{1}{N} \sum_{j=1}^N \mathbb{E}[\mathbb{I}_{(z_j=i)} \mid \mathbf{x}, \theta_n]$$

$$\hat{\mu}_i = \frac{\sum_{j=1}^N x_j \mathbb{E}[\mathbb{I}_{(z_j=i)} \mid \mathbf{x}, \theta_n]}{\sum_{j=1}^N \mathbb{E}[\mathbb{I}_{(z_j=i)} \mid \mathbf{x}, \theta_n]}$$

où $z_j$ est la classe cachée de l'observation $j$ (voir [[Variables cachées d'un modèle de mélange]]), $\mathbf{x}$ l'ensemble des observations et $\theta_n$ l'estimation des paramètres à l'itération $n$.

# Interprétation

Chaque espérance $\mathbb{E}[\mathbb{I}_{(z_j=i)} \mid \mathbf{x}, \theta_n]$ est la [[Probabilité d'appartenance à une classe|probabilité d'appartenance]] de l'observation $j$ à la composante $i$ : dans ces estimateurs, une observation contribue à chaque composante proportionnellement à sa probabilité d'y appartenir.

L'[[Espérance-maximisation pour un mélange de gaussiennes|espérance-maximisation]] se comporte ainsi comme une version à appartenance douce du [[k-means]] : chaque observation est répartie sur les composantes, tandis que le k-means l'affecte à un unique cluster (voir [[Algorithme des k-moyennes de Lloyd]]).

# Exemple

Sur les mêmes données, réparties en deux classes figurées par une ellipse rouge et une ellipse bleue, la comparaison de l'espérance-maximisation et du k-means illustre la différence de traitement de l'appartenance :

- côté espérance-maximisation, chaque point est dessiné comme un disque dont les parts rouge et bleue traduisent sa répartition entre les deux classes ;
- côté k-means, chaque point est entièrement coloré selon le cluster auquel il est affecté.

# Remarque

Lorsque les appartenances $z_j$ sont connues, les espérances $\mathbb{E}[\mathbb{I}_{(z_j=i)} \mid \mathbf{x}, \theta_n]$ se réduisent aux indicatrices $\mathbb{I}_{(z_j=i)}$ : on retrouve les estimateurs du maximum de vraisemblance à données complètes, donnés dans [[Estimation par maximum de vraisemblance d'un modèle de mélange]].

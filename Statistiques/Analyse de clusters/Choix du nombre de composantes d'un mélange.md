# Interprétation

Le nombre de composantes $K$ d'un [[Modèles de mélange|mélange]] doit être choisi : deux approches sont possibles, l'expérimentation ou un critère d'information.

Un **critère d'information** sert à comparer des modèles de complexités différentes en combinant leur ajustement aux données et une pénalité de complexité :

$$\mathcal{I}(\mathbf{x}, \theta) = \ln p(\mathbf{x}; \theta) - g(\#\text{parameters}, \#\text{data})$$

- $\ln p(\mathbf{x}; \theta)$ mesure l'ajustement du modèle aux données par la [[Fonction de vraisemblance|log-vraisemblance]] ;
- $g(\#\text{parameters}, \#\text{data})$ est une pénalité qui dépend du nombre de paramètres du modèle et du nombre de données.

Plus un mélange compte de composantes, plus il compte de paramètres : un [[Mélange gaussien|mélange gaussien]] a ainsi pour paramètres des poids, des moyennes et des covariances. Le premier terme mesure l'ajustement du modèle aux données, le second pénalise la complexité ; le critère arbitre ainsi entre les deux lorsque $K$ varie.

Parmi ces critères figurent le critère d'Akaike, le [[Critère d'information bayésien|critère d'information bayésien]] (BIC) et d'autres encore. Le BIC s'écrit

$$\operatorname{BIC}(x, \theta) = \ln p(x \mid \theta) - \frac{1}{2}\#\theta \ln n$$

où $\#\theta$ est le nombre de paramètres et $n$ la taille de l'échantillon : la pénalité est d'autant plus forte que le modèle compte de paramètres.

# Remarque

Le choix du nombre de composantes d'un mélange relève de la [[Sélection de modèle et estimation de la performance|sélection de modèle]]. La démarche analogue pour un [[k-means]] est décrite dans [[Choix du nombre de clusters]].

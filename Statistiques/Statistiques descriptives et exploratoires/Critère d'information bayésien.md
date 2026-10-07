# Définition

Le **critère d'information bayésien** (BIC, *Bayesian information criterion*) est un critère utilisé pour la [[Sélection de modèle et estimation de la performance|sélection de modèle]] : choix d'une famille de distributions, du nombre de composantes, etc. Il est défini par

$$\operatorname{BIC}(x, \theta) = \ln p(x \mid \theta) - \frac{1}{2}\#\theta \ln n$$

où $x$ désigne les données observées, $\theta$ les paramètres du modèle, $\#\theta$ le nombre de paramètres et $n$ la taille de l'échantillon.

# Interprétation

Le BIC s'utilise dans le cadre de l'[[Estimation bayésienne]] pour comparer des modèles de complexités différentes. Il combine deux termes :

- $\ln p(x \mid \theta)$ mesure l'ajustement du modèle aux données par la log-vraisemblance, que maximise l'[[Estimateur du maximum de vraisemblance|estimateur du maximum de vraisemblance]] ;
- $-\frac{1}{2}\#\theta \ln n$ pénalise la complexité du modèle : la pénalité est d'autant plus forte que le modèle compte de paramètres $\#\theta$.

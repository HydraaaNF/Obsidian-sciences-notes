# Définition

Pour un échantillon unique $\mathbf{o}$, la **densité des données complètes** $(\mathbf{o}, \mathbf{s})$ d'un [[Modèle de Markov caché]] (la [[Probabilités d'un modèle de Markov caché|loi jointe]] de la suite des états et de la suite des observations) a pour logarithme

$$\ln p(\mathbf{o}, \mathbf{s}) = \ln(\pi_{s_1}) + \sum_{t=2}^{T} \ln(a_{s_{t-1}s_t}) + \sum_{t=1}^{T} \ln(b_{s_t}(o_t)),$$

où $N$ est le nombre d'états et $T$ la longueur de la séquence, $\pi_i$ la probabilité que l'état initial soit $i$, $a_{ij}$ la probabilité de passer de l'état $i$ à l'état $j$ et $b_i(o_t)$ la probabilité d'émission de l'observation $o_t$ dans l'état $i$ (voir [[Paramètres d'un modèle de Markov caché]]).

Ce logarithme se réécrit à l'aide de fonctions indicatrices :

$$\ln p(\mathbf{o}, \mathbf{s}) = \sum_{i=1}^{N} \ln(\pi_i) \mathbb{I}_{(s_1=i)} + \sum_{t=2}^{T} \sum_{i,j=1}^{N} \ln(a_{ij}) \mathbb{I}_{(s_{t-1}=i, s_t=j)} + \sum_{t=1}^{T} \sum_{i=1}^{N} \ln(b_i(o_t)) \mathbb{I}_{(s_t=i)}$$

En remplaçant chaque indicatrice par son [[Espérance conditionnelle|espérance conditionnelle]] sachant les observations $\mathbf{o}$, pour les paramètres courants $\theta_n$, on obtient la **fonction auxiliaire de l'espérance-maximisation** du modèle :

$$\begin{aligned} Q(\theta, \theta_n) &= \sum_{i=1}^{N} \ln(\pi_i) \mathbb{E}[\mathbb{I}_{(s_1=i)} \mid \mathbf{o}; \theta_n] + \sum_{i,j=1}^{N} \ln(a_{ij}) \left( \sum_{t=2}^{T} \mathbb{E}[\mathbb{I}_{(s_{t-1}=i,s_t=j)} \mid \mathbf{o}; \theta_n] \right) \\ &+ \sum_{i=1}^{N} \sum_{t=1}^{T} \ln(b_i(o_t)) \mathbb{E}[\mathbb{I}_{(s_t=i)} \mid \mathbf{o}; \theta_n] \end{aligned}$$

Elle se décompose en trois termes, relatifs aux probabilités initiales, aux probabilités de transition et aux probabilités d'émission du modèle.

# Remarque

Le terme d'émission de la densité des données complètes associe, à chaque instant $t$, l'observation $o_t$ à l'état $s_t$ : il s'écrit $\sum_{t=1}^{T} \ln(b_{s_t}(o_t))$ et, sous forme indicatrice, $\sum_{i=1}^{N} \ln(b_i(o_t))\,\mathbb{I}_{(s_t=i)}$. Les écritures $\sum_{t=1}^{T} \ln(b_{s_1}(o_1))$ (le même terme $b_{s_1}(o_1)$ répété à chaque instant) et $b_i(o_k)$ (indice $k$ absent des sommations) sont des erreurs à éviter : les indices de l'état et de l'observation doivent être ceux de l'instant courant $t$.

La fonction auxiliaire est la spécialisation au [[Modèle de Markov caché]] de la [[Fonction auxiliaire de l'algorithme d'espérance-maximisation|fonction auxiliaire générale]] de l'[[Algorithme d'espérance-maximisation|algorithme d'espérance-maximisation]] ; c'est elle que maximise l'[[Algorithme de Baum-Welch]] pour réestimer les paramètres du modèle ([[Réestimation des paramètres d'un modèle de Markov caché]]).

# Définition

Soit un [[Modèle de Markov caché|modèle de Markov caché]] de paramètres $\lambda_N$. Pour une séquence d'observations donnée $\mathbf{o} = o_1, \dots, o_T$, le **décodage d'une séquence d'états** consiste à calculer efficacement la séquence d'états $\mathbf{s} = s_1, \dots, s_T$ pour laquelle la probabilité de cette séquence d'observations est maximale, c'est-à-dire

$$\hat{\mathbf{s}} = \arg \max_{s_1, \dots, s_T} \mathbb{P}[o_1, \dots, o_T \mid s_1, \dots, s_T; \lambda_N]\,\mathbb{P}[s_1, \dots, s_T; \lambda_N].$$

La probabilité jointe ainsi maximisée s'exprime en fonction des [[Paramètres d'un modèle de Markov caché|paramètres du modèle]] : voir [[Probabilités d'un modèle de Markov caché]].

# Propriétés

Dans le domaine logarithmique, on cherche à maximiser la log-probabilité jointe des séquences d'observations et d'états :

$$\begin{aligned}
\ln \mathbb{P}[\mathbf{o}, \mathbf{s}] &= \ln(\pi_{s_1}) + \ln(b_{s_1}(o_1)) + \sum_{t=2}^{T} \left( \ln(a_{s_{t-1}s_t}) + \ln(b_{s_t}(o_t)) \right) \\
&= \ln(\pi_{s_1}) + \ln(b_{s_1}(o_1)) + \ln(a_{s_1s_2}) + \ln(b_{s_2}(o_2)) + \ln(a_{s_2s_3}) + \ln(b_{s_3}(o_3)) + \ln(a_{s_3s_4}) + \ln(b_{s_4}(o_4)) + \cdots
\end{aligned}$$

# Interprétation

Le décodage recherche la séquence d'états cachés la plus vraisemblable au vu des observations. La maximisation de la log-probabilité jointe est résolue efficacement par un algorithme de programmation dynamique, qui recherche le meilleur chemin dans un [[Treillis|treillis]] : c'est l'[[Algorithme de Viterbi]].

# Remarque

Le décodage d'une séquence d'états correspond au premier des [[Trois problèmes d'un modèle de Markov caché]].

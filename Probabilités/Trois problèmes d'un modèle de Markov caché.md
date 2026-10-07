# Définition

Un [[Modèle de Markov caché|modèle de Markov caché]] de paramètres $\lambda_N$ conduit à trois problèmes :

1. **Trouver la séquence d'états la plus probable.** Étant donné un modèle $\lambda_N$, comment calculer efficacement la séquence d'états $\mathbf{s} = s_1, \dots, s_T$ pour laquelle la probabilité d'une séquence d'observations donnée $\mathbf{o} = o_1, \dots, o_T$ est maximale ?
2. **Évaluer la probabilité d'une séquence d'observations.** Étant donné un modèle $\lambda_N$, comment calculer efficacement la probabilité d'une séquence d'observations donnée $\mathbf{o} = o_1, \dots, o_T$ ?
3. **Estimer les paramètres.** Étant donné un ensemble de séquences d'apprentissage, comment estimer efficacement les paramètres d'un modèle $\lambda_N$ selon le critère du maximum de vraisemblance ?

# Remarque

- Le premier problème est l'objet du [[Décodage d'une séquence d'états]].
- L'évaluation de la probabilité d'une séquence d'observations repose sur l'algorithme forward-backward : voir [[Calcul des espérances par l'algorithme forward-backward]].
- Le troisième problème est celui de l'estimation des paramètres : voir [[Estimation empirique des paramètres d'un modèle de Markov caché]].

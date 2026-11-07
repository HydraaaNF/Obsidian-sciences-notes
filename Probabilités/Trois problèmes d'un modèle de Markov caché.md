#adm-6 #adm-7

# Définition

Un [[Modèle de Markov caché|modèle de Markov caché]] de paramètres $\lambda_N$ décrit une séquence d'états $s = s_1, \ldots, s_T$ et une séquence d'observations $o = o_1, \ldots, o_T$. Trois problèmes se posent à son sujet.

## Décodage de la séquence d'états la plus probable

Le modèle $\lambda_N$ étant donné, comment calculer efficacement la séquence d'états $s = s_1, \ldots, s_T$ pour laquelle la probabilité d'une séquence d'observations donnée $o = o_1, \ldots, o_T$ est maximale ?

## Évaluation de la probabilité d'une séquence d'observations

Le modèle $\lambda_N$ étant donné, comment calculer efficacement la probabilité d'une séquence d'observations donnée $o = o_1, \ldots, o_T$ ?

## Estimation des paramètres

Un ensemble de séquences d'apprentissage étant donné, comment estimer efficacement les paramètres d'un modèle $\lambda_N$ au sens du critère du maximum de vraisemblance ?

# Interprétation

Les deux premiers énoncés prennent le modèle $\lambda_N$ en donnée ; le troisième prend un ensemble de séquences d'apprentissage et a pour inconnue les paramètres du modèle. Tous partagent la même exigence : un calcul efficace.

- La séquence d'états la plus probable, pour une séquence d'observations donnée : c'est un problème de décodage.
- La probabilité d'une séquence d'observations, sans se prononcer sur les états : c'est un problème d'évaluation du modèle sur des données.
- Les paramètres du modèle eux-mêmes, à partir de séquences d'apprentissage : c'est un problème d'estimation.

# Remarque

Chacun des trois problèmes a sa méthode propre.

- Le décodage est traité par le [[Décodage d'une séquence d'états|décodage d'une séquence d'états]], résolu par l'[[Algorithme de Viterbi|algorithme de Viterbi]] qui explore un [[Treillis|treillis]].
- L'évaluation de la probabilité d'une séquence d'observations est la somme des quantités de l'[[Algorithme forward|algorithme forward]] ; les [[Probabilités forward et backward|probabilités forward et backward]] servent aussi au calcul des espérances conditionnelles.
- L'estimation par maximum de vraisemblance s'appuie sur l'[[Estimation par maximum de vraisemblance d'un modèle de Markov|estimation par maximum de vraisemblance]] et, quand les séquences d'états sont connues, sur l'[[Estimation empirique des paramètres d'un modèle de Markov caché|estimation empirique des paramètres]] ; sinon l'[[Algorithme de Baum-Welch|algorithme de Baum-Welch]] alterne le [[Calcul des espérances par l'algorithme forward-backward|calcul des espérances par l'algorithme forward-backward]] et la maximisation.

Les trois problèmes portent sur les mêmes quantités de base, les [[Probabilités d'un modèle de Markov caché|probabilités d'un modèle de Markov caché]], dont les facteurs sont les [[Paramètres d'un modèle de Markov caché|paramètres du modèle]].

Le décodage y maximise cette loi jointe sur les suites d'états, l'évaluation la somme sur ces suites, et l'estimation en ajuste les facteurs.

# Algorithme

L'**algorithme segmental k-means** estime les [[Paramètres d'un modèle de Markov caché|paramètres]] $\theta$ d'un [[Modèle de Markov caché|modèle de Markov caché]] $\lambda_N$ à partir d'échantillons d'entraînement. Il procède par itérations :

1. Partir de valeurs initiales $\theta_0$ des paramètres.
2. Effectuer le [[Décodage d'une séquence d'états|décodage]] de chaque échantillon d'entraînement, c'est-à-dire déterminer sa meilleure séquence d'états, celle qui maximise la probabilité jointe des observations et des états :

$$\widehat{\mathbf{s}}^{(r)} = \arg \max_{\mathbf{s}} \mathbb{P}\left[o_1^{(r)}, \ldots, o_T^{(r)} \mid s_1, \ldots, s_T; \lambda_N(\theta_n)\right] \mathbb{P}\left[s_1, \ldots, s_T; \lambda_N(\theta_n)\right]$$

3. Calculer de nouvelles estimations $\theta_{n+1}$ des paramètres au moyen des [[Estimation empirique des paramètres d'un modèle de Markov caché|estimateurs empiriques]], connaissant les alignements obtenus.
4. Répéter les étapes 2 et 3 jusqu'à satisfaction.

# Interprétation

L'algorithme alterne ainsi deux phases : la détermination de la séquence d'états la plus probable pour chaque échantillon, puis la réestimation des paramètres à partir des alignements obtenus. Il s'agit d'un algorithme d'[[Algorithme d'espérance-maximisation|espérance-maximisation]], qui compense les variables manquantes, ici les séquences d'états non observées.

# Remarque

L'algorithme segmental k-means transpose au cas séquentiel l'alternance de l'[[Algorithme des k-moyennes de Lloyd|algorithme des k-moyennes de Lloyd]] (affectation, puis mise à jour) et constitue une alternative à l'[[Algorithme de Baum-Welch]].

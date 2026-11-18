#dmv-pattern_mining_vs_deep_learning

# Algorithme

L'apprentissage de l'[[Auto-encodeur de motifs]] parcourt les transactions $X$ de la base $D$ et répète pour chacune quatre étapes :

1. **Reconstruction** : la passe avant fait traverser le réseau à l'entrée, $X \longrightarrow W_b^\top \longrightarrow b_d \longrightarrow W_b \longrightarrow X'$.
2. **Calcul de la perte** : la perte $L_{W,b}(X)$ mesure l'écart entre la reconstruction $X'$ et l'entrée $X$.
3. **Rétropropagation** : la passe arrière calcule les gradients de la perte par rapport aux poids et au biais.
4. **Bornage** : les poids continus $W$ sont projetés sur $W_b$ binarisé, et les biais continus $b$ sur $b_d$ discrétisé.

Dans la passe avant, $W_b^\top$ porte les poids d'encodage vers la [[Couche de motifs]], $b_d$ le biais, $W_b$ les poids de décodage, et $X'$ est la reconstruction de l'entrée $X$.

Les gradients calculés à l'étape 3 sont les dérivées de la perte par rapport aux poids,

$$\frac{dL_{W,b}(X)}{dW}$$

et par rapport au biais,

$$\frac{dL_{W,b}(X)}{db}$$

La passe arrière traverse d'abord les poids de décodage $W$, puis le biais $b$, puis les poids d'encodage $W^\top$ : le gradient remonte le chemin inverse de la passe avant, du décodage vers l'encodage.

Le [[Fonction de bornage dans un intervalle|bornage]] de l'étape 4 ne clôt pas l'apprentissage : les paramètres binarisés $W_b$ et discrétisés $b_d$ obtenus sont réutilisés à l'étape 1 de l'itération suivante, si bien que la binarisation des poids et la discrétisation du biais sont réappliquées à chaque tour de boucle. Cette alternance entre optimisation continue et paramètres binaires est le sujet de [[Poids binaires et optimisation différentiable]].

# Remarque

La passe arrière de cette boucle est une [[Rétropropagation]] sur le graphe de calcul de l'auto-encodeur : elle part de la perte $L_{W,b}(X)$, remonte les opérations de décodage puis d'encodage, et y applique la règle de la chaîne pour obtenir les dérivées par rapport à $W$ et à $b$.

Cet ordre de traversée est parfois énoncé dans le sens inverse, $W^\top$ puis $W$ : la passe avant applique les poids d'encodage $W^\top$ avant les poids de décodage $W$, si bien que le gradient, qui les rencontre en remontant, passe par $W$ puis par $W^\top$.

Les paramètres $W$ et $b$ sont partagés par toutes les transactions : chaque tour de boucle calcule donc un gradient pour la transaction courante, et c'est l'accumulation de ces gradients sur $D$ qui décrit l'effet global des paramètres.

La perte $L_{W,b}(X)$ n'est pas l'écart de reconstruction brut : sa forme exacte, qui pondère chaque item selon la parcimonie de la base, est donnée dans [[Perte de reconstruction pondérée par la parcimonie]].

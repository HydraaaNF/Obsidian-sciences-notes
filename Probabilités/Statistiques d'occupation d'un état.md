# Définition

Dans un [[Modèle de Markov caché]], la **statistique d'occupation** de l'état $i$ au temps $t$ est la probabilité conditionnelle

$$\begin{aligned} \gamma_t(i) &= \mathbb{P}[S_t = i \mid o_1, \dots, o_T] \\ &= \frac{\mathbb{P}[o_1, \dots, o_t, S_t = i]\, \mathbb{P}[o_{t+1}, \dots, o_T \mid S_t = i]}{\mathbb{P}[o_1, \dots, o_T]} \\ &= \frac{\alpha_i(t)\beta_i(t)}{\sum_{i=1}^N \alpha_i(t)\beta_i(t)}, \end{aligned}$$

où $\alpha_i(t)$ et $\beta_i(t)$ sont les [[Probabilités forward et backward|probabilités forward et backward]] de l'état $i$ au temps $t$ et où la somme du dénominateur porte sur les $N$ états.

# Interprétation

$\gamma_t(i)$ est la probabilité que l'état occupé au temps $t$ soit l'état $i$, calculée une fois connue la séquence complète des observations $o_1, \dots, o_T$ : elle mesure l'**occupation** de l'état $i$ au cours du temps.

Le dénominateur $\sum_{i=1}^N \alpha_i(t)\beta_i(t)$ vaut la probabilité $\mathbb{P}[o_1, \dots, o_T]$ de la séquence d'observations, et le numérateur en est le terme associé à l'état $i$.

# Remarque

- La statistique d'occupation est l'analogue temporel de la [[Probabilité d'appartenance à une classe]] : elle exprime la probabilité conditionnelle de l'état occupé au temps $t$ sachant toute la séquence d'observations.
- Son calcul relève du [[Calcul des espérances par l'algorithme forward-backward|calcul des espérances par l'algorithme forward-backward]] ; la statistique jumelle décrivant les changements d'état est la [[Statistiques de transition entre deux états|statistique de transition entre deux états]].

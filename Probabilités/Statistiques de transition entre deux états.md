# Définition

Soient un [[Modèle de Markov caché|modèle de Markov caché]] à $N$ états et une séquence d'observations $o_1, \dots, o_T$. La **statistique de transition entre deux états** est la probabilité jointe que l'état caché soit $i$ à l'instant $t-1$ et $j$ à l'instant $t$, conditionnellement à la séquence complète des observations :

$$\begin{aligned}\xi_t(i,j) &= \mathbb{P}[S_{t-1} = i,\ S_t = j \mid o_1, \dots, o_T] \\ &= \frac{\mathbb{P}[o_1^{t-1}, S_{t-1} = i]\mathbb{P}[o_t, S_t = j \mid S_{t-1} = i]\mathbb{P}[o_{t+1}^T \mid S_t = j]}{\mathbb{P}[o_1, \dots, o_T]} \\ &= \frac{\alpha_i(t-1)a_{ij}b_j(o_t)\beta_j(t)}{\sum_{i=1}^N \alpha_i(t)\beta_i(t)}\end{aligned}$$

où $\alpha_i(t-1)$ et $\beta_j(t)$ sont les [[Probabilités forward et backward|probabilités forward et backward]], $a_{ij}$ la probabilité de transition de l'état $i$ vers l'état $j$, $b_j(o_t)$ la probabilité d'observer $o_t$ dans l'état $j$ et $N$ le nombre d'états.

# Remarque

Avec la [[Statistiques d'occupation d'un état|statistique d'occupation d'un état]] $\gamma_t(i)$, la statistique de transition $\xi_t(i,j)$ fait partie des espérances dont le calcul est mené par l'[[Calcul des espérances par l'algorithme forward-backward|algorithme forward-backward]].

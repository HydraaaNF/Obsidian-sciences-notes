# Définition

L'estimation des paramètres d'un [[Modèle de Markov caché]] fait intervenir deux espérances, pour une séquence d'observations $\mathbf{o}$ et une estimation courante $\theta_n$ des paramètres :

$$\gamma_t^{(r)}(i) = \mathbb{E}\left[\mathbb{I}_{(s_t=i)} \mid \mathbf{o}; \theta_n\right] = \mathbb{P}[S_t = i]$$

et

$$\xi_t^{(r)}(i,j) = \mathbb{E}\left[\mathbb{I}_{\left(s_{t-1}^{(r)}=i,\ s_t^{(r)}=j\right)} \mid \mathbf{o}; \theta_n\right] = \mathbb{P}[S_{t-1}=i,\ S_t=j].$$

La première est la probabilité de l'évènement $S_t = i$ ; la seconde est la probabilité jointe des évènements $S_{t-1}=i$ et $S_t=j$. Le problème est alors leur calcul efficace.

# Remarque

- $\gamma_t^{(r)}(i)$ est la [[Statistiques d'occupation d'un état|statistique d'occupation d'un état]] et $\xi_t^{(r)}(i,j)$ la [[Statistiques de transition entre deux états|statistique de transition entre deux états]] ; ces espérances sont évaluées à l'étape E de l'[[Algorithme de Baum-Welch]].
- Le calcul efficace de ces quantités est l'objet de l'algorithme forward-backward : voir [[Probabilités forward et backward]], [[Algorithme forward]] et [[Algorithme backward]].

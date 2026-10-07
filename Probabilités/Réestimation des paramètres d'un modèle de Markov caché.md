# Propriétés

Les [[Paramètres d'un modèle de Markov caché|paramètres]] d'un [[Modèle de Markov caché|modèle de Markov caché]] sont réestimés par [[Méthode du maximum de vraisemblance|maximum de vraisemblance]] à partir de $R$ échantillons d'observations $\mathbf{o}^{(r)}$ de longueurs $n_r$. En respectant les contraintes de normalisation $\sum_i \pi_i = 1$, $\sum_j a_{ij} = 1$ et $\sum_k b_{ik} = 1$, les formules de réestimation s'écrivent :

$$\hat{\pi}_i = \frac{\sum_r \gamma_1^{(r)}(i)}{R}$$

$$\hat{a}_{ij} = \frac{\sum_r \sum_{t=2}^{n_r} \xi_t^{(r)}(i,j)}{\sum_r \sum_{t=1}^{n_r-1} \gamma_t^{(r)}(i)}$$

$$\hat{b}_{ik} = \frac{\sum_r \sum_{t=1}^{n_r} \mathbb{I}_{(o_t^{(r)}=k)} \gamma_t^{(r)}(i)}{\sum_r \sum_{t=1}^{n_r} \gamma_t^{(r)}(i)}$$

où les [[Statistiques d'occupation d'un état|statistiques d'occupation]] et les [[Statistiques de transition entre deux états|statistiques de transition]] sont les espérances

$$\gamma_t^{(r)}(i) = \mathbb{E}[\mathbb{I}_{(s_t^{(r)}=i)} \mid \mathbf{o}; \theta_n]$$

$$\xi_t^{(r)}(i,j) = \mathbb{E}[\mathbb{I}_{(s_{t-1}^{(r)}=i, s_t^{(r)}=j)} \mid \mathbf{o}; \theta_n]$$

Ces formules correspondent à l'étape de maximisation de l'[[Algorithme de Baum-Welch]].

Pour des densités continues, les moyennes sont réestimées par les formules suivantes.

Pour une [[Loi gaussienne|densité gaussienne]] :

$$\mu_i = \frac{\sum_{t=1}^{T} \gamma_t(i)o_t}{\sum_{t=1}^{T} \gamma_t(i)}$$

Pour un [[Mélange gaussien|mélange gaussien]] :

$$\mu_{ij} = \frac{\sum_{t=1}^{T} \gamma_t(i,j)\,o_t}{\sum_{t=1}^{T} \gamma_t(i,j)}$$

avec

$$\gamma_t(i,j) = \frac{\alpha_i(t)\beta_i(t)}{\sum_{i=1}^{N}\alpha_i(t)\beta_i(t)}\frac{w_{ij}\mathcal{N}(o_t;\mu_{ij},\sigma_{ij})}{\sum_{k=1}^{K}w_{ik}\mathcal{N}(o_t;\mu_{ik},\sigma_{ik})}$$

où $\alpha_i(t)$ et $\beta_i(t)$ sont les [[Probabilités forward et backward|probabilités forward et backward]] et $\mathcal{N}$ une densité gaussienne.

# Remarque

- La distribution initiale décrit l'état de départ de chaque échantillon : le numérateur de $\hat{\pi}_i$ est la somme des statistiques d'occupation du premier instant, $\sum_r \gamma_1^{(r)}(i)$. Sommer les statistiques d'occupation de tous les instants, $\sum_r \sum_t \gamma_t^{(r)}(i)$, est une erreur fréquente, cette forme ne respecte pas la contrainte de normalisation $\sum_i \pi_i = 1$.
- La mise à jour des moyennes pour un [[Mélange gaussien|mélange gaussien]] est détaillée dans l'[[Espérance-maximisation pour un mélange de gaussiennes]].

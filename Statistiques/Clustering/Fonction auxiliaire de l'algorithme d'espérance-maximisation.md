# Définition

L'[[Algorithme d'espérance-maximisation|algorithme d'espérance-maximisation]] vise à maximiser une **fonction auxiliaire**, définie par

$$Q(\theta, \hat{\theta}) = \mathbb{E}[\ln f(\mathbf{z}, \mathbf{x}; \theta) | \mathbf{x}; \hat{\theta}]$$

où $f(z, x; \theta)$ est la [[Fonction de vraisemblance|vraisemblance]] des données complètes, formées des observations $\mathbf{x}$ et de leurs [[Variables cachées d'un modèle de mélange|classes cachées]] $\mathbf{z}$, et où l'espérance est prise conditionnellement aux observations, pour la valeur courante $\hat{\theta}$ des paramètres.

# Algorithme

La fonction auxiliaire est exploitée par les deux étapes de l'algorithme :

- **Étape E (estimation)** : calculer les quantités espérées dans $Q(\theta, \hat{\theta})$ (sachant $\hat{\theta} = \theta_n$) ;
- **Étape M (maximisation)** : maximiser la fonction auxiliaire par rapport aux (vrais) paramètres $\theta$ (sachant les quantités espérées), pour obtenir une nouvelle estimation $\hat{\theta} = \theta_{i+1}$ :

$$\theta_{i+1} = \arg\max_{\theta} Q(\theta, \theta_i)$$

# Propriétés

Pour un échantillon de taille $n$, $\mathbf{x} = \{x_1, \dots, x_n\}$, et une estimation courante $\hat{\theta}$ des paramètres $\theta$ à estimer, la fonction auxiliaire d'un [[Modèles de mélange|mélange]] à $K$ composantes se développe en

$$Q(\theta, \hat{\theta}) = \sum_{j=1}^K \sum_{i=1}^n \ln(\pi_j) \mathbb{E}_{\hat{\theta}}[\mathbb{I}_{(j=z_i)} | \mathbf{x}] + \ln(p_{\theta_j}(x_i)) \mathbb{E}_{\hat{\theta}}[\mathbb{I}_{(j=z_i)} | \mathbf{x}]$$

### Démonstration

La log-vraisemblance des données complètes s'écrit

$$\begin{aligned}\ln f_{\theta}(\mathbf{z}, \mathbf{x}) &= \ln \left( \prod_{i=1}^n \mathbb{P}_{\theta}[Z_i = z_i] p_{\theta}(x_i \mid z_i) \right) \\ &= \sum_{i=1}^n \ln \underbrace{\mathbb{P}_{\theta}[Z_i = z_i]}_{=\pi_{z_i}} + \ln \underbrace{p_{\theta}(x_i \mid z_i)}_{\text{par exemple, }\mathcal{N}(\mu_{z_i}, \sigma_{z_i})} \\ &= \sum_{j=1}^K \sum_{i=1}^n \ln(\pi_j)\mathbb{I}_{(j=z_i)} + \ln\bigl(p_{\theta_j}(x_i)\bigr)\mathbb{I}_{(j=z_i)} \end{aligned}$$

En prenant l'[[Espérance conditionnelle|espérance conditionnelle]] sachant $\mathbf{x}$ sous $\hat{\theta}$, chaque indicatrice devient son espérance et l'on obtient la forme ci-dessus.

La maximisation de $Q(\theta, \hat{\theta})$ par rapport à $\pi_j$, sous la contrainte que les poids somment à 1, donne

$$\hat{\pi}_j \leftarrow \frac{\sum_i \mathbb{E}_{\hat{\theta}}[\mathbb{I}_{(z_i=j)} \mid \mathbf{x}]}{\sum_k \sum_i \mathbb{E}_{\hat{\theta}}[\mathbb{I}_{(z_i=k)} \mid \mathbf{x}]}.$$

De même, la maximisation par rapport aux paramètres $\theta_j$ de la log-vraisemblance de la $j$-ième composante, $\ln(p_{\theta_j}(x_i))$, donne une fonction des espérances $\mathbb{E}_{\hat{\theta}}[\mathbb{I}_{(z_i=j)} | \mathbf{x}]$ ; par exemple, pour une densité gaussienne (voir [[Espérance-maximisation pour un mélange de gaussiennes]]) :

$$\hat{\mu}_j \leftarrow \frac{\sum_i x_i \mathbb{E}_{\hat{\theta}}[\mathbb{I}_{(z_i=j)} \mid \mathbf{x}]}{\sum_i \mathbb{E}_{\hat{\theta}}[\mathbb{I}_{(z_i=j)} \mid \mathbf{x}]}.$$

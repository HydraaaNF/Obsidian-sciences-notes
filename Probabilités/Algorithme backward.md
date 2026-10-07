# Algorithme

L'**algorithme backward** calcule les [[Probabilités forward et backward|probabilités backward]] $\beta_i(t)$ d'un [[Modèle de Markov caché]] de paramètres $\lambda_N(\theta)$. La quantité backward se calcule récursivement selon

$$\mathbb{P}[o_{t+1}, \ldots, o_T \mid S_t = i] = \sum_{j=1}^{N} \mathbb{P}[o_{t+1}, S_{t+1} = j \mid S_t = i]\,\mathbb{P}[o_{t+2}, \ldots, o_T \mid S_{t+1} = j].$$

**Initialisation** ($t = T$) :

$$\beta_i(T) = 1 \quad \forall i \in [1, N].$$

**Récursion** (pour $t = 2, \ldots, T$ et $j = 1, \ldots, N$) :

$$\beta_i(t) = \sum_{j=1}^{N} a_{ij} b_j(o_{t+1}) \beta_j(t+1).$$

On note que

$$\mathbb{P}[o_1, \ldots, o_t; \lambda_N(\theta)] = \sum_{i=1}^{N} \pi_i \beta_i(1).$$

# Remarque

- L'algorithme backward est le symétrique de l'[[Algorithme forward]] : les deux parcourent les observations en sens inverse l'un de l'autre et s'appuient sur la même structure de [[Treillis]].

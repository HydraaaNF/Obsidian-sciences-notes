# Algorithme

Pour un [[Mélange gaussien|mélange gaussien]] à $K$ composantes, l'[[Algorithme d'espérance-maximisation|algorithme d'espérance-maximisation]] prend une forme explicite, en fonction des densités $f(x_i; \mu_j, \sigma_j)$ des composantes et des [[Variables cachées d'un modèle de mélange|classes cachées]] $z_i$.

La vraisemblance jointe des observations $\mathbf{x}$ et des classes cachées $\mathbf{z}$ est

$$\ln f(\mathbf{x}, \mathbf{z}) = \sum_{i=1}^N \sum_{j=1}^K \ln(w_j f(x_i; \mu_j, \sigma_j)) \mathbb{I}_{(z_i=j)}$$

La [[Fonction auxiliaire de l'algorithme d'espérance-maximisation|fonction auxiliaire]] associée vaut

$$Q(\theta, \theta_n) \propto \sum_{j=1}^K \sum_{i=1}^N \ln(w_j) \mathbb{E}[\mathbb{I}_{(z_i=j)} \mid \mathbf{x}; \theta_n] - \frac{1}{2} \sum_{j=1}^K \sum_{i=1}^N \left( \sum_{k=1}^d \ln(\sigma_{jk}^2) + \frac{(x_{ik} - \mu_{jk})^2}{\sigma_{jk}^2} \right) \mathbb{E}[\mathbb{I}_{(z_i=j)} \mid \mathbf{x}; \theta_n]$$

À l'itération $n$, le calcul des espérances donne la [[Probabilité d'appartenance à une classe|probabilité d'appartenance]] d'une observation $x_i$ à la composante $j$ :

$$\gamma_j^{(n)}(i) = \frac{w_j^{(n)} f(x_i; \mu_j^{(n)}, \sigma_j^{(n)})}{\sum_k w_k^{(n)} f(x_i; \mu_k^{(n)}, \sigma_k^{(n)})}$$

où les paramètres correspondent à l'estimation courante $\theta^{(n)}$.

La maximisation met ensuite à jour les poids et les moyennes :

$$w_j^{(n+1)} = \frac{\sum_{i=1}^N \gamma_j^{(n)}(i)}{\sum_{k=1}^K \sum_{i=1}^N \gamma_k^{(n)}(i)}$$

$$\mu_{jk}^{(n+1)} = \frac{\sum_{i=1}^N \gamma_j^{(n)}(i) x_{ik}}{\sum_{i=1}^N \gamma_j^{(n)}(i)}$$

# Remarque

$Q(\theta, \theta_n)$ est la forme prise par la [[Fonction auxiliaire de l'algorithme d'espérance-maximisation|fonction auxiliaire]] dans le cas du [[Mélange gaussien|mélange gaussien]], et $\gamma_j^{(n)}(i)$ la [[Probabilité d'appartenance à une classe|probabilité d'appartenance]] d'une observation à une composante.

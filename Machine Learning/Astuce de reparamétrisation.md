#ml-2

# Définition

L'astuce de reparamétrisation remplace le tirage direct d'un plongement $\mathbf{z}$ dans la loi de moyenne $\boldsymbol{\mu}(\mathbf{x})$ et d'écart-type $\boldsymbol{\sigma}(\mathbf{x})$ par une transformation déterministe d'un bruit standard :

$$\mathbf{z} = \boldsymbol{\mu}(\mathbf{x}) + \boldsymbol{\sigma}(\mathbf{x}) \odot \boldsymbol{\varepsilon}, \qquad \boldsymbol{\varepsilon} \sim \mathcal{N}(0, I)$$

Le produit $\odot$ est élément par élément, et $\boldsymbol{\varepsilon}$ est un bruit de même dimension que $\mathbf{z}$, tiré dans une loi normale centrée réduite indépendante de l'entrée et des paramètres du réseau.

# Interprétation

Le tirage direct coupe le gradient du terme de reconstruction. Prélever un échantillon dans $q(\mathbf{z} \mid \mathbf{x})$ est une opération aléatoire dont le résultat dépend des paramètres seulement à travers la loi, sans chemin différentiable qui les relie : le gradient du terme de reconstruction, qui passe par la reconstruction $\hat{\mathbf{x}} = d(\mathbf{z})$, ne peut pas traverser l'opération de tirage.

La réécriture déplace tout l'aléa dans $\boldsymbol{\varepsilon}$. Une fois $\boldsymbol{\varepsilon}$ tiré, $\mathbf{z}$ devient une fonction déterministe de $\boldsymbol{\mu}(\mathbf{x})$ et de $\boldsymbol{\sigma}(\mathbf{x})$, donc des paramètres de l'encodeur : le gradient traverse $\boldsymbol{\mu}$ et $\boldsymbol{\sigma}$ et redescend jusqu'à eux. Composante par composante, $z_i = \mu_i + \sigma_i \varepsilon_i$, d'où $\partial z_i/\partial \mu_i = 1$ et $\partial z_i/\partial \sigma_i = \varepsilon_i$, les dérivées croisées étant nulles : les jacobiennes valent $\partial \mathbf{z}/\partial \boldsymbol{\mu} = I$ et $\partial \mathbf{z}/\partial \boldsymbol{\sigma} = \operatorname{diag}(\boldsymbol{\varepsilon})$. C'est ce qui rend l'[[Auto-encodeur variationnel]] entraînable par [[Rétropropagation]] et [[Différenciation automatique]], puisque le [[Graphe de calcul]] contient désormais une chaîne continue de l'entrée à la perte.

La privation de gradient ne porte toutefois que sur le terme de reconstruction. Le terme de divergence KL ne dépend que de $\boldsymbol{\mu}$ et de $\boldsymbol{\sigma}$, pas de l'échantillon $\mathbf{z}$ : son gradient, $\partial \operatorname{KL}/\partial \mu_i = \mu_i$ et $\partial \operatorname{KL}/\partial \sigma_i = \sigma_i - 1/\sigma_i$, s'écrit directement en fonction de ces paramètres et atteint encore l'encodeur, qu'il pousse vers la loi $\mathcal{N}(0, I)$.

# Algorithme

Entraînement :

1. l'encodeur fournit les paramètres de la loi latente : $\mathbf{x} \rightarrow \boldsymbol{\mu}(\mathbf{x}), \boldsymbol{\sigma}(\mathbf{x})$ ;
2. tirer le bruit standard : $\boldsymbol{\varepsilon} \sim \mathcal{N}(0, I)$ ;
3. construire l'échantillon : $\mathbf{z} = \boldsymbol{\mu}(\mathbf{x}) + \boldsymbol{\sigma}(\mathbf{x}) \odot \boldsymbol{\varepsilon}$ ;
4. le décodeur reconstruit : $\hat{\mathbf{x}} = d(\mathbf{z})$ ;
5. optimiser la perte, somme du terme de reconstruction et du terme de divergence KL, par rétropropagation à travers $\boldsymbol{\mu}$ et $\boldsymbol{\sigma}$.

Génération :

1. oublier l'encodeur ;
2. tirer $\mathbf{z} \sim \mathcal{N}(0, I)$ ;
3. renvoyer $d(\mathbf{z})$.

# Remarque

Le terme de divergence KL garde l'espace latent « rempli » : il ramène les lois $q(\mathbf{z} \mid \mathbf{x})$ vers $\mathcal{N}(0, I)$, de sorte que tout $\mathbf{z}$ tiré de $\mathcal{N}(0, I)$ se décode en quelque chose de plausible, y compris entre les moyennes associées aux exemples d'entraînement.

Sans l'astuce, l'échantillonnage reste possible en passe avant, mais le gradient du terme de reconstruction ne traverse pas le tirage : le modèle ne peut pas être optimisé de bout en bout, seul le terme KL continuant de fournir un gradient à l'encodeur.

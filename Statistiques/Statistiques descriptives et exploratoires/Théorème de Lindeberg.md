# Théorème

Soit $X_1, \ldots, X_n$ des [[Variable aléatoire|variables aléatoires]] [[Indépendance de variables aléatoires|indépendantes]], de moyennes $\mu_i$ et d'écarts-types $\sigma_i$. Sous certaines conditions,

$$\frac{\sum_i (X_i - \mu_i)}{\sqrt{\sum_i \sigma_i^2}} \to \mathcal{N}(0,1)$$

où $\mathcal{N}(0,1)$ désigne la [[Loi gaussienne|loi gaussienne]] centrée réduite et où la convergence s'entend au sens de la [[Convergence en loi|convergence en loi]].

# Interprétation

La somme normalisée tend vers une [[Loi gaussienne|variable aléatoire gaussienne]] centrée réduite : c'est une généralisation du [[Théorème de la limite centrale]] au cas de variables indépendantes non nécessairement de même loi.

# Remarque

Le théorème de Lindeberg généralise le [[Théorème de la limite centrale]] : les variables ne sont pas supposées de même loi (les moyennes $\mu_i$ et les écarts-types $\sigma_i$ peuvent différer d'une variable à l'autre) mais elles doivent être indépendantes et vérifier certaines conditions.

Le numérateur de la formule centre la somme par son espérance : il s'écrit $\sum_i (X_i - \mu_i)$, soit $\sum_i X_i - \sum_i \mu_i$. Une écriture qui ne retranche qu'un seul terme de moyenne à la somme, du type $\sum_i X_i - m_i$, ne centre pas celle-ci et laisse le symbole $m_i$ non défini : les moyennes des $X_i$ sont les $\mu_i$. La forme correcte est $\sum_i (X_i - \mu_i)$.

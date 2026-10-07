# Propriétés

Une [[Projection linéaire des données|projection linéaire]] des données est d'autant meilleure qu'elle satisfait les critères suivants :

- **conserver inchangées, autant que possible, les distances entre individus** ;
- **maximiser la variance** des données projetées ;
- **maximiser l'inertie** des données projetées ;
- **minimiser l'erreur des moindres carrés**.

L'inertie des données projetées vérifie l'identité

$$\text{Trace}(\mathbf{Y}^\top\mathbf{Y}) = \text{Trace}(\mathbf{VP})$$

# Interprétation

Sur un [[Nuage de points|nuage de points]], les directions mises en avant sont la **première composante principale**, le long de l'axe d'étirement du nuage, et la **deuxième composante principale**, qui lui est orthogonale.

Ces quatre critères sont équivalents dans le cadre de l'ACP classique : ils sont ceux que met en œuvre l'[[Analyse en composantes principales]], et les sous-espaces qui les satisfont sont caractérisés par les [[Théorèmes de l'analyse en composantes principales]].

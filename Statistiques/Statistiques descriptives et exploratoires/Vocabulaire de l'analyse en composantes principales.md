# Définition

En [[Analyse en composantes principales|analyse en composantes principales]] (ACP), on appelle :

- **axe principal** (ou **facteur**) le vecteur $\mathbf{u}_i$, une combinaison linéaire des variables descriptives ;
- **composante principale** le vecteur $\mathbf{c}_i = \mathbf{X}\mathbf{u}_i$, homogène à une variable : c'est la [[Projection linéaire des données|projection linéaire]] des données sur le $i$-ème axe principal.

Chaque composante principale s'écrit aussi explicitement comme combinaison linéaire des variables descriptives :

$$\mathbf{c}_i = \sum_{j=1}^{p} u_{ij}\,\mathbf{x}_j$$

Les composantes principales sont non corrélées entre elles.

En résumé, l'ACP remplace les variables corrélées $\mathbf{x}_1 \dots \mathbf{x}_p$ par de nouvelles variables, les composantes principales $\mathbf{c}_1 \dots \mathbf{c}_q$, combinaisons linéaires non corrélées des variables $\mathbf{x}_i$ avec variance maximale.

# Propriétés

- La variance de la composante principale $\mathbf{c}_i$ est la valeur propre associée : $\mathbb{V}[\mathbf{c}_i] = \lambda_i$.
- Les composantes principales sont les vecteurs propres de la matrice $(n, n)$ $\mathbf{X}\mathbf{X}^\top$ ; ce résultat les relie à l'espace des variables.

# Interprétation

Les données forment un tableau de $n$ individus décrits par $p$ variables. Les composantes principales forment un second tableau de $n$ individus, chaque colonne étant une composante principale, c'est-à-dire une nouvelle variable.

- Le **premier plan principal** est le plan des deux premières composantes principales ; chaque individu y est représenté par ses coordonnées sur ces deux composantes.
- La **carte des variables** situe les variables descriptives par leurs corrélations avec les deux premières composantes principales.

# Remarque

Il existe une différence entre axe et facteur lorsqu'une métrique $M \neq I$ est utilisée.

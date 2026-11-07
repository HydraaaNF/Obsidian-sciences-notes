#adm-8

# Définition

Étant donnée une information testable (ou a priori) connue sur les données, la meilleure distribution de probabilité pour ces données est celle dont l'[[Entropie d'une variable aléatoire discrète|entropie]] est maximale sous les contraintes imposées par cette information.

L'information testable prend notamment les formes suivantes :

- la connaissance de certains moments, par exemple la moyenne de $x$ vaut $0{,}25$ ;
- la connaissance a priori de certaines probabilités, par exemple $p(1) = 0{,}25$ ou $p(1) + p(3) = 0{,}4$.

Le principe s'écrit comme un programme d'optimisation : maximiser $H(p)$ sur l'ensemble des distributions qui satisfont les contraintes connues.

# Interprétation

Parmi les distributions compatibles avec ce que l'on sait des données, celle d'entropie maximale est la moins informative : elle n'ajoute aucune hypothèse que les faits observés ne justifient pas.

Toute autre distribution compatible introduirait de l'information supplémentaire, donc un biais non justifié. Réciproquement, le principe exploite toute l'information disponible : chaque fait connu devient une contrainte, et la distribution retenue est la plus proche possible de l'ignorance totale sous ces contraintes.

# Exemple

Les distributions de maximum d'entropie usuelles sont les suivantes :

- sous la seule contrainte d'un support fini et d'une masse totale égale à $1$, la [[Loi uniforme discrète|loi uniforme discrète]], et plus généralement les distributions uniformes par morceaux lorsque des contraintes fixent la masse de certains groupes de valeurs ;
- pour une moyenne et un écart-type fixés, la [[Loi gaussienne|loi gaussienne]] ;
- pour une moyenne fixée égale à $1/\lambda$ sur les valeurs positives, la [[Loi exponentielle|loi exponentielle]] de paramètre $\lambda$.

# Remarque

Ces familles ne relèvent pas toutes du même type de contrainte. La loi uniforme discrète est déterminée par la seule contrainte de support, avec une masse totale égale à $1$ et aucun moment fixé ; les distributions uniformes par morceaux fixent de plus la masse de certains groupes de valeurs. Les lois gaussienne et exponentielle relèvent, elles, de contraintes de moment : moyenne et variance fixées pour la première, moyenne fixée sur $\mathbb{R}_+$ pour la seconde.

En modélisation, ces contraintes sont souvent fournies par des estimations empiriques sur les données d'entraînement, pour la spécification du modèle. Ce sont alors des espérances empiriques calculées sur ces données, ce qui conduit à une distribution de [[Forme exponentielle d'une distribution de maximum d'entropie|forme exponentielle]]. Le cas d'un modèle de traduction est détaillé dans [[Distribution de maximum d'entropie d'une traduction]], et la formulation générale des contraintes dans [[Contraintes d'espérance sur les fonctions de traits]].

#dmv-xai

# Modèle

Le modèle linéaire décrit la variable à expliquer comme une combinaison affine des attributs, à un terme d'erreur près. Ses coefficients sont les paramètres que l'apprentissage doit déterminer.

$$y_i = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \ldots + \beta_n x_n + \epsilon_i$$

Chaque attribut $x_j$ entre avec son coefficient $\beta_j$, $\beta_0$ est la constante du modèle et $\epsilon_i$ le terme d'erreur de l'observation $i$.

En rassemblant les attributs de l'observation $i$ dans un vecteur $\mathbf{x}_i$ et les coefficients dans un vecteur $\boldsymbol{\beta}$, la même équation tient en une seule ligne :

$$y_i = \mathbf{x}_i^\top \boldsymbol{\beta} + \varepsilon_i$$

Cette écriture est celle de la [[Forme matricielle de la régression]], qui transporte la même règle de calcul aux sorties vectorielles et aux lots d'observations.

Le cas d'un attribut unique et d'une constante se réduit à une droite, la [[Droite de régression de y en x|droite de régression de y en x]] : le modèle linéaire en est la forme à plusieurs attributs.

# Interprétation

La prédiction est une somme de contributions additives : un terme par attribut, dont le coefficient fixe le poids, plus une constante qui fixe le niveau de la prédiction lorsque tous les attributs sont nuls. Le signe d'un coefficient donne le sens de la contribution, sa valeur donne l'ampleur du déplacement de la prédiction pour une unité de l'attribut.

C'est ce qui fait du modèle linéaire une boîte de verre : l'équation ajustée est elle-même l'explication, sans outil ajouté, comme le décrit l'[[Interprétabilité]] et, par contraste, l'[[Explicabilité]].

# Exemple

Une régression linéaire ajustée sur trois attributs s'écrit

$$y = -189.69 - 0.0002 \times cases + 2.39 \times score + 5.08 \times age$$

| Terme | Coefficient |
|---|---|
| constante | $-189.69$ |
| $cases$ | $-0.0002$ |
| $score$ | $2.39$ |
| $age$ | $5.08$ |

L'équation se lit terme à terme : la constante place le niveau de base, $age$ et $score$ poussent la prédiction vers le haut, $cases$ la tire vers le bas avec un coefficient d'ampleur négligeable.

# Algorithme

Les coefficients ne sont pas posés à la main : ils s'obtiennent en minimisant l'écart entre les valeurs observées et les valeurs ajustées. La somme des carrés des résidus, pour des observations $\mathbf{y}$ et une matrice de conception $\mathbf{X}$, vaut

$$S(\beta) = \sum_{i=1}^{n}\left| y_i - \sum_{j=1}^{p} X_{ij}\beta_j \right|^2 = \|\mathbf{y} - \mathbf{X}\boldsymbol{\beta}\|^2$$

où $n$ est le nombre d'observations et $p$ le nombre d'attributs.

### Moindres carrés ordinaires

Les moindres carrés ordinaires (OLS) retiennent les coefficients qui minimisent cette somme des carrés des résidus, sans autre contrainte.

### LASSO

Le LASSO minimise la même somme des carrés des résidus, mais sous une contrainte portant sur les coefficients :

$$\min_{\beta_0,\boldsymbol{\beta}} \left\{ \|y - \beta_0 - X\boldsymbol{\beta}\|_2^2 \right\}$$

sous la contrainte

$$\|\boldsymbol{\beta}\|_1 \le t$$

La norme $\|\cdot\|_1$ est la somme des valeurs absolues des coefficients : le seuil $t$ borne cette somme, donc la taille globale du vecteur des coefficients.

# Remarque

- La même forme linéaire, privée de son terme d'erreur, sert de score dans le [[Lien logistique comme modèle interprétable]] : $y'_i$ y est la combinaison affine des attributs, ensuite transformée par la sigmoïde en une probabilité.
- Un coefficient ne se lit qu'à unité d'attribut fixée : deux coefficients d'ampleurs très différentes peuvent décrire des effets comparables si les attributs ne sont pas exprimés dans la même unité. La lecture agrégée de la contribution d'un attribut sur tout un jeu de données est l'objet de l'[[Importance des variables par agrégation]].
- L'ajustement suit la démarche de la [[Régression linéaire]] : une perte est minimisée sur les données observées, et les moindres carrés en sont la version quadratique. Le seuil $t$ du LASSO borne la somme des valeurs absolues des coefficients, là où les moindres carrés ordinaires n'imposent aucune borne.
- L'ajustement suppose des données étiquetées, dont chaque exemple porte sa valeur cible, voir l'[[Apprentissage à partir de données étiquetées]].
- Une famille linéaire s'étend en modèles à base de règles, plus expressifs et toujours lisibles, voir les [[Règles, listes et ensembles de décision]].
- La linéarité impose ses limites : interactions et effets non monotones lui échappent, ce que recensent en partie les [[Questions ouvertes de l'explicabilité]].

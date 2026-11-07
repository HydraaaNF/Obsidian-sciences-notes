#adm-8

# Définition

Soit $f_i(x, y)$ une fonction de trait dépendant d'une observation $x$ et d'une étiquette $y$, et soit $\tilde{p}$ la distribution empirique des couples $(x, y)$ observés dans les données d'entraînement. L'espérance empirique de $f_i$ est la moyenne de la fonction de trait sur ces couples :

$$\mathbb{E}[f_i(x, y)] = \sum_{x,y} f_i(x, y)\,\tilde{p}(x, y)$$

La loi jointe empirique se décompose en $\tilde{p}(x, y) = \tilde{p}(x)\,p(y \mid x)$, produit de la distribution empirique des observations par la distribution conditionnelle des étiquettes, de sorte que la même quantité s'écrit aussi

$$\mathbb{E}[f_i(x, y)] = \sum_{x,y} f_i(x, y)\,\tilde{p}(x)\,p(y \mid x)$$

Cette valeur, notée $F_i$, est la proportion empirique de la configuration repérée par le trait dans les données.

# Propriétés

Pour un trait binaire à valeurs dans $\{0, 1\}$, la somme ne retient que les couples où le trait vaut $1$ :

$$\mathbb{E}[f_i(x, y)] = \tilde{p}(\{(x,y) \mid f_i(x, y) = 1\})$$

L'espérance empirique d'un indicateur n'est donc rien d'autre que la fréquence empirique de la configuration qu'il repère.

La contrainte de modélisation associée impose que l'[[Espérance d'une variable aléatoire|espérance]] théorique du trait sous la distribution du modèle $\mathbb{P}$ reproduise cette valeur observée :

$$\mathbb{E}_{\mathbb{P}}[f_i(X, Y)] = F_i$$

# Exemple

Dans un problème de traduction, les fonctions de traits sont des indicateurs binaires. Un trait peut repérer la configuration « la sortie est *en* et le mot *April* suit le mot *in* » :

$$f_i(x, y) = \begin{cases} 1 & \text{si } y = \text{en} \text{ et } \textit{April} \text{ suit } \textit{in} \\ 0 & \text{sinon} \end{cases}$$

On veut alors que $\mathbb{E}[f_i(x, y)]$ soit égal à la proportion empirique de cette configuration dans les données d'entraînement, c'est-à-dire que la probabilité de l'observer sous le modèle coïncide avec la fréquence observée. Le calcul se réduit à la somme des $\tilde{p}(x, y)$ portant sur les couples vérifiant la condition, d'où l'égalité avec $F_i$.

# Remarque

- L'espérance empirique est une donnée du problème, calculée une fois sur les couples d'entraînement ; c'est elle qui fournit le membre de droite $F_i$ des contraintes décrites dans [[Contraintes d'espérance sur les fonctions de traits]].
- Dans le cadre conditionnel d'un [[Modèle log-linéaire conditionnel]], le trait dépend à la fois de $x$ et de $y$, et l'espérance empirique se compare à l'espérance conditionnelle du modèle pour chaque observation.
- L'écart entre l'espérance empirique et l'espérance théorique est précisément ce qui pilote la mise à jour des paramètres lors de l'estimation par maximum de vraisemblance : voir [[Gradient de la vraisemblance conditionnelle]].
- Un jeu complet de traits binaires et les contraintes qu'ils induisent sur une distribution sont détaillés dans [[Fonctions de traits d'un exemple de traduction]].

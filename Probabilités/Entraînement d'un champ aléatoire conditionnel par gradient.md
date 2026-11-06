# Algorithme

L'estimation des paramètres d'un [[Champ aléatoire conditionnel à chaîne linéaire|champ aléatoire conditionnel à chaîne linéaire]] se fait par montée de gradient sur la [[Vraisemblance conditionnelle d'un champ aléatoire conditionnel|vraisemblance conditionnelle]]. Pour chaque couple d'apprentissage $(x^{(r)}, y^{(r)})$, en partant d'une estimation courante $\Lambda$ des paramètres et avec un pas d'apprentissage $\alpha > 0$ :

1. calculer, ou estimer, l'espérance $\mathbb{E}[f_i(x, y) \mid x^{(r)}; \Lambda]$ de chaque fonction de traits sous la loi conditionnelle courante, l'espérance portant sur les étiquettes $y$ ;
2. calculer la valeur $f_i(x^{(r)}, y^{(r)})$ du trait sur les étiquettes réellement observées ;
3. mettre à jour chaque paramètre par montée de gradient :

$$
\lambda_i \leftarrow \lambda_i + \alpha \left( f_i(x^{(r)}, y^{(r)}) - \mathbb{E}[f_i(x, y) \mid x^{(r)}; \Lambda] \right)
$$

Le calcul de l'espérance de l'étape 1 se fait de façon efficace par l'[[Calcul des espérances par l'algorithme forward-backward|algorithme forward-backward]], qui exploite la structure de chaîne pour éviter d'énumérer les suites d'étiquettes (voir [[Probabilités forward et backward]]).

La boucle parcourt les couples du jeu d'apprentissage, l'estimation $\Lambda$ étant remplacée par sa valeur mise à jour à chaque étape.

# Interprétation

Le terme entre parenthèses compare deux quantités pour le même trait :

- $f_i(x^{(r)}, y^{(r)})$ est ce que le trait vaut sur les étiquettes observées, c'est-à-dire la [[Espérance empirique d'une fonction de trait|valeur empirique]] du trait sur l'exemple ;
- $\mathbb{E}[f_i(x, y) \mid x^{(r)}; \Lambda]$ est ce que le modèle courant prédit en moyenne pour ce même trait sur toutes les suites d'étiquettes possibles, observations $x^{(r)}$ fixées.

La mise à jour déplace donc chaque paramètre dans la direction qui réduit l'écart entre le comportement observé et le comportement prédit : un trait qui apparaît plus souvent dans les étiquettes réelles que ne le prédit le modèle voit son poids $\lambda_i$ augmenter, un trait surestimé par le modèle voit son poids diminuer. Quand le modèle reproduit déjà les valeurs observées, le terme correctif tend vers zéro et les paramètres se stabilisent ; c'est cette condition d'équilibre que traduit l'annulation du [[Gradient de la vraisemblance conditionnelle|gradient de la vraisemblance conditionnelle]].

# Remarque

L'entraînement est plus complexe en pratique que cette boucle de montée de gradient.

- Une régularisation de l'objectif est nécessaire, pour éviter que les paramètres ne prennent des valeurs excessives sur des traits rares.
- D'autres méthodes d'optimisation du gradient que la montée de gradient simple sont employées, par exemple la méthode BFGS.
- L'espérance de l'étape 1 n'est pas nécessairement calculée exactement : l'échantillonnage de Gibbs et l'*iterative scaling* en fournissent des solutions de remplacement au forward-backward.

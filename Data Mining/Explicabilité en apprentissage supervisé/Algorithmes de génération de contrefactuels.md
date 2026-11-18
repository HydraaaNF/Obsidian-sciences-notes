#dmv-xai

# Définition

Un **algorithme de génération de contrefactuels** calcule, pour une instance $x$ et un modèle $f$, une instance $e$ du domaine des entrées dont la prédiction par le modèle diffère de celle de $x$ : $f(e) \neq f(x)$. Le contrefactuel n'est pas fourni par le modèle : il est cherché dans l'espace des entrées, par une procédure de recherche ou d'optimisation, après l'entraînement.

# Modèle

La recherche s'écrit comme la minimisation d'un coût sous la contrainte que la prédiction change de classe.

$$e^* = \arg\min_{e \in \mathcal{X}} \{ c(x,e) \mid f(e) \neq f(x) \}$$

Le coût agrège la distance et la parcimonie de la modification.

$$c(x,e) = \|x - e\|_2 + \gamma \|x - e\|_0$$

- la contrainte $f(e) \neq f(x)$ impose à $e$ de franchir la frontière de décision : le contrefactuel obtenu est valide par construction.
- le terme $\|x - e\|_2$ mesure l'éloignement en amplitude, donc la proximité du contrefactuel à l'instance d'origine.
- le terme $\|x - e\|_0$ compte le nombre de variables modifiées, donc la parcimonie de la modification.
- le poids $\gamma$ arbitre entre proximité et parcimonie.

# Algorithme

## Growing Spheres

La recherche se fait en deux étapes dans une hypersphère centrée sur l'instance cible. La première part d'un grand rayon, puis contracte l'hypersphère autour de $x$ jusqu'à ce qu'elle ne couvre plus aucun contrefactuel, donc jusqu'à ne contenir que des points de la classe d'origine. La seconde agrandit la sphère centrée sur $x$ jusqu'à franchir la frontière de décision, donc jusqu'à couvrir une instance de l'autre classe. L'algorithme minimise ainsi à la fois la distance et la parcimonie, ce que traduit le coût $c(x,e)$.

## FACE

FACE (*feasible and actionable counterfactuals*) évite les contrefactuels situés dans des régions de faible densité. Le contrefactuel le plus proche au sens de la distance peut tomber dans une zone où aucune observation n'a été relevée, donc peu crédible pour l'utilisateur. FACE retient au contraire un déplacement qui traverse des régions denses en données, quitte à parcourir un trajet plus long. Sur une classification à deux classes, quatre candidats A à D sont atteints par des trajets rectilignes depuis l'instance d'origine : C et D tombent dans des nuages denses de la classe opposée, A dans la bande de transition, et B reste isolé dans une zone sans observation.

## DICE

DICE sélectionne un ensemble de contrefactuels selon deux critères, la diversité et la parcimonie. Il peut en outre encoder des contraintes fixées par l'utilisateur, par exemple qu'un enfant ne demande pas de crédit ou que la taille d'une personne est vraisemblablement immuable. Il est conçu pour les données tabulaires.

$$C(x) = \arg\min_{c_1,\dots,c_k} \frac{1}{k}\sum_{i=1}^{k} \mathrm{yloss}(f(c_i), y) + \frac{\lambda_1}{k}\sum_{i=1}^{k} \mathrm{dist}(c_i, x) - \lambda_2\,\mathrm{dpp\_diversity}(c_1,\dots,c_k)$$

- le premier terme mesure l'écart entre la prédiction de chaque candidat $c_i$ et la classe visée $y$.
- le deuxième terme mesure la distance de chaque candidat à l'instance d'origine, avec le poids $\lambda_1$.
- le troisième terme, retranché avec le poids $\lambda_2$, récompense la diversité de l'ensemble : il évite de proposer $k$ variantes presque identiques.

# Propriétés

Les trois procédures ne contrôlent pas les mêmes qualités du contrefactuel.

- Growing Spheres minimise la distance et le nombre de variables modifiées, sans terme lié à la densité des données.
- FACE privilégie la plausibilité en écartant les contrefactuels situés dans des régions de faible densité.
- DICE produit un ensemble de candidats diversifiés et parcimonieux, sous contraintes utilisateur, pour des données tabulaires.

La proximité et la plausibilité se compensent : la modification la plus proche de l'instance d'origine peut se trouver dans une zone où les données sont rares, alors qu'un déplacement plus long mais passant par des observations réelles est plus facile à accepter. Le choix de la méthode arbitre ce compromis.

# Remarque

La validité du contrefactuel, assurée par la seule contrainte $f(e) \neq f(x)$, ne dit rien de sa plausibilité : une modification portant sur une unique variable peut être invraisemblable, par exemple une taille de personne. Les contraintes utilisateur de DICE et le critère de densité de FACE répondent à cette limite, que le coût de Growing Spheres ne couvre pas.

Aucune de ces procédures ne garantit l'optimum global du coût ni l'unicité du contrefactuel : elles produisent un ou plusieurs candidats, que l'utilisateur arbitre. D'autres contrefactuels sont obtenus sans recherche, par un réseau entraîné à les générer : voir [[Réseaux de neurones contrefactuels]] et [[Apprentissage de contrefactuels]]. La même construction étendue à un groupe d'instances donne les [[Contrefactuels globaux]], et le cas des documents relève des [[Contrefactuels pour le texte]]. Ces méthodes sont une forme d'[[Explication contrefactuelle]], à situer par rapport à l'[[Explication locale]].

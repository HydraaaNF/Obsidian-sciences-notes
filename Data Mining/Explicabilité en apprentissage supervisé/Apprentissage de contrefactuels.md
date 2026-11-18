#dmv-xai

# Définition

L'**apprentissage de contrefactuels** désigne l'obtention d'une instance contrefactuelle par minimisation d'une fonction de perte, qui arbitre le compromis entre sparsité et cohérence de distribution.

# Modèle

La ressemblance à des prototypes est imposée dans un espace latent, obtenu par un [[Auto-encodeur]] dont l'encodeur est noté $\mathrm{ENC}$.

Le prototype de référence pour l'instance d'origine $x_0$ est celui dont le code est le plus proche, à l'exclusion de l'indice $t_0$ :

$$j = \arg\min_{i \neq t_0} \left\| \mathrm{ENC}(x_0) - \mathrm{proto}_i \right\|_2$$

Le contrefactuel est cherché sous la forme $x_0+\delta$ : la perte porte sur la perturbation $\delta$ de l'instance d'origine, et mesure l'écart entre le code de cette instance modifiée et celui du prototype retenu :

$$L_{\mathrm{proto}} = \theta \cdot \left\| \mathrm{ENC}(x_0+\delta) - \mathrm{proto}_j \right\|_2^2$$

Le coefficient $\theta$ pondère le terme de prototype dans la perte.

# Propriétés

Trois exigences pèsent sur le contrefactuel produit.

- la **validité** : la prédiction du contrefactuel diffère de celle de l'instance d'origine ;
- la **sparsité** : le contrefactuel ne modifie qu'une partie des variables de l'instance d'origine ;
- la **cohérence de distribution** : le contrefactuel reste proche des instances typiques, résumées ici par les prototypes de l'espace latent.

La perte arbitre le compromis entre les deux dernières exigences, la validité étant la condition d'obtention d'un contrefactuel.

Le terme de prototype porte la cohérence de distribution : plus $\theta$ est grand, plus l'éloignement du code au prototype pèse dans la perte.

Plusieurs fonctions de perte, notées $A$ à $F$, conduisent à des contrefactuels différents pour une même instance d'origine.

# Exemple

Sur des chiffres manuscrits, une instance d'origine donne six contrefactuels, obtenus avec six fonctions de perte distinctes notées $A$ à $F$.

Ces contrefactuels sont aussi présentés après reconstruction par l'auto-encodeur, ce qui montre le rendu obtenu une fois le code latent ramené dans l'espace des entrées.

# Remarque

La démarche décrite ci-dessus résout une optimisation pour chaque instance traitée. Un générateur appris en est une variante : il produit le contrefactuel par une passe avant une fois entraîné, le coût se déplaçant de l'usage vers l'apprentissage.

L'instance obtenue reste une [[Explication contrefactuelle]] et une [[Explication locale]], dont elle ne change que le mode d'obtention. Un [[Réseaux de neurones contrefactuels|réseau contrefactuel]] apprend conjointement la prédiction et l'explication, alors que les [[Algorithmes de génération de contrefactuels]] recherchent l'instance directement dans l'espace des entrées.

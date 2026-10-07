# Définition

Trois [[Évènement|évènements]] $A$, $B$ et $C$ sont **mutuellement indépendants** si :

1. $\mathbb{P}[A \cap B \cap C] = \mathbb{P}[A]\mathbb{P}[B]\mathbb{P}[C]$ ;
2. $\mathbb{P}[A \cap B] = \mathbb{P}[A]\mathbb{P}[B]$ ;
3. $\mathbb{P}[A \cap C] = \mathbb{P}[A]\mathbb{P}[C]$ ;
4. $\mathbb{P}[B \cap C] = \mathbb{P}[B]\mathbb{P}[C]$.

Cette définition s'étend : $n$ évènements $A_1, \dots, A_n$ sont mutuellement indépendants si et seulement si, pour chaque ensemble de $k \in [2, n]$ indices distincts $i_1, \dots, i_k$ ($i_j \in [1, n]$ pour tout $j$),

$$\mathbb{P}[A_{i_1} \cap A_{i_2} \cap \dots \cap A_{i_k}] = \mathbb{P}[A_{i_1}]\mathbb{P}[A_{i_2}] \dots \mathbb{P}[A_{i_k}].$$

# Exemple

On lance deux dés équilibrés ; l'[[Espace probabilisé|univers]] des issues est $\Omega = \{(i, j) \mid 1 \leq i, j \leq 6\}$.

## Exemple 1

- $A$ : le premier dé donne $1$, $2$ ou $3$, donc $\mathbb{P}[A] = \frac{3}{6}$ ;
- $B$ : le premier dé donne $3$, $4$ ou $5$, donc $\mathbb{P}[B] = \frac{3}{6}$ ;
- $C$ : la somme vaut $9$, donc $\mathbb{P}[C] = \frac{4}{36}$.

On a bien

$$\mathbb{P}[A \cap B \cap C] = \frac{1}{36} = \mathbb{P}[A]\mathbb{P}[B]\mathbb{P}[C],$$

mais

$$\mathbb{P}[A \cap B] = \frac{6}{36} \neq \frac{9}{36} = \mathbb{P}[A]\mathbb{P}[B].$$

L'inégalité tient aussi pour $A \cap C$ et $B \cap C$ : $A$, $B$ et $C$ ne sont donc pas mutuellement indépendants, bien que l'égalité $\mathbb{P}[A \cap B \cap C] = \mathbb{P}[A]\mathbb{P}[B]\mathbb{P}[C]$ soit vérifiée.

## Exemple 2

- $A$ : le premier dé donne $1$, $2$ ou $3$, donc $\mathbb{P}[A] = \frac{3}{6}$ ;
- $B$ : le second dé donne $4$, $5$ ou $6$, donc $\mathbb{P}[B] = \frac{3}{6}$ ;
- $C$ : la somme vaut $7$, donc $\mathbb{P}[C] = \frac{6}{36}$.

Les évènements $A$, $B$ et $C$ sont deux à deux indépendants, mais

$$\mathbb{P}[A \cap B \cap C] = \frac{1}{12} \neq \frac{1}{24} = \mathbb{P}[A]\mathbb{P}[B]\mathbb{P}[C].$$

Ils ne sont donc pas mutuellement indépendants.

# Remarque

- L'indépendance mutuelle **généralise l'[[Indépendance de deux évènements|indépendance de deux évènements]]** : pour $n = 2$, la définition se réduit à l'unique condition $\mathbb{P}[A \cap B] = \mathbb{P}[A]\mathbb{P}[B]$. L'indépendance de deux évènements s'énonce à partir de la [[Probabilité conditionnelle]] ; l'indépendance mutuelle se caractérise directement par les égalités de produits, exigées pour *tous* les sous-ensembles d'indices, de taille $2$ à $n$.
- Dans le produit des $k$ probabilités, chacun des indices $i_1, \dots, i_k$ apparaît une fois : la forme correcte est $\mathbb{P}[A_{i_1}]\mathbb{P}[A_{i_2}] \dots \mathbb{P}[A_{i_k}]$. Omettre l'un des indices (par exemple écrire $\mathbb{P}[A_{i_1}]\mathbb{P}[A_{i_3}] \dots \mathbb{P}[A_{i_k}]$, où le facteur d'indice $i_2$ manque) est une erreur d'indice fréquente : le produit ne compte alors que $k - 1$ facteurs et ne peut pas être égal à la probabilité de l'intersection des $k$ évènements.

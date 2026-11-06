# Modèle

On cherche à traduire le mot anglais *in* en français. La variable aléatoire $Y$ prend ses valeurs dans l'ensemble des traductions possibles :

$$\{\text{dans}, \text{en}, \text{à}, \text{au cours de}, \text{pendant}\}.$$

On note $p(y) = \mathbb{P}(Y = y)$ la probabilité attribuée à chaque traduction, et $p(\text{dans})$ s'écrit de même pour chaque valeur. Les faits connus sur les données sont encodés par quatre fonctions de traits, chacune indicatrice d'une propriété de la traduction :

- $f_1(y) = 1$ pour toute traduction $y$ ;
- $f_2(y) = \mathbb{1}[y \in \{\text{dans}, \text{en}\}]$ ;
- $f_3(y) = \mathbb{1}[y \in \{\text{à}, \text{au cours de}, \text{pendant}\}]$ ;
- $f_4(y) = \mathbb{1}[y \in \{\text{dans}, \text{à}\}]$.

Chaque trait vaut $1$ lorsque la traduction possède la propriété décrite et $0$ sinon : $f_2$ repère les traductions « dans » et « en », $f_3$ les trois autres, $f_4$ deux traductions prises dans des groupes différents.

# Propriétés

Les contraintes d'espérance associées à ces traits fixent la masse de probabilité des groupes qu'ils décrivent :

$$\mathbb{E}_Y[f_1(Y)] = p(\text{dans}) + p(\text{en}) + p(\text{à}) + p(\text{au cours de}) + p(\text{pendant}) = 1$$

$$\mathbb{E}_Y[f_2(Y)] = p(\text{dans}) + p(\text{en}) = \frac{3}{10}$$

$$\mathbb{E}_Y[f_3(Y)] = p(\text{à}) + p(\text{au cours de}) + p(\text{pendant}) = \frac{7}{10}$$

$$\mathbb{E}_Y[f_4(Y)] = p(\text{dans}) + p(\text{à}) = \frac{1}{2}$$

L'espérance d'un trait binaire se réduit à la somme des probabilités des valeurs pour lesquelles il vaut $1$, ce qui donne directement ces quatre équations. La forme générale de ces contraintes est décrite dans [[Contraintes d'espérance sur les fonctions de traits]].

# Interprétation

Chaque contrainte exprime un fait observé sur les données sous forme d'une masse de probabilité :

- $f_2$ et $f_3$ séparent les cinq traductions en deux groupes disjoints, de masses respectives $3/10$ et $7/10$ ;
- $f_4$ relie deux traductions appartenant à des groupes différents : la masse conjointe de « dans » et « à » vaut $1/2$ ;
- le trait constant $f_1$ ne distingue aucune traduction, sa contrainte n'est autre que la somme des probabilités égale à un.

Les quatre contraintes portent donc sur des sous-ensembles qui se chevauchent : « dans » intervient dans trois d'entre elles, ce qui conduit à une distribution dont les probabilités ne sont pas uniformes par groupes.

# Loi

Sous ces quatre contraintes, la distribution de [[Principe du maximum d'entropie|maximum d'entropie]] de $Y$ est

$$\mathbb{P}(Y = y) = \frac{1}{Z(\hat{\Lambda})} \exp\left(\hat{\lambda}_1 f_1(y) + \hat{\lambda}_2 f_2(y) + \hat{\lambda}_3 f_3(y) + \hat{\lambda}_4 f_4(y)\right)$$

où $\hat{\Lambda} = \{\hat{\lambda}_1, \dots, \hat{\lambda}_4\}$ est le jeu de multiplicateurs qui maximise l'entropie conditionnelle $H(Y \mid \Lambda)$ sous les quatre contraintes, et où $Z(\hat{\Lambda})$ normalise la distribution. La construction de cette distribution sur le même exemple est détaillée dans [[Distribution de maximum d'entropie d'une traduction]], et sa forme générale dans [[Forme exponentielle d'une distribution de maximum d'entropie]].

# Exemple

Les valeurs des traits s'additionnent pour chaque traduction. Pour « dans », les traits $f_1$, $f_2$ et $f_4$ valent $1$, tandis que $f_3$ vaut $0$ :

$$\mathbb{P}(Y = \text{dans}) = \frac{1}{Z(\hat{\Lambda})} \exp\left(\hat{\lambda}_1 + \hat{\lambda}_2 + \hat{\lambda}_4\right)$$

Pour « pendant », seuls $f_1$ et $f_3$ valent $1$ :

$$\mathbb{P}(Y = \text{pendant}) = \frac{1}{Z(\hat{\Lambda})} \exp\left(\hat{\lambda}_1 + \hat{\lambda}_3\right)$$

La probabilité d'une traduction ne dépend ainsi que des multiplicateurs des traits qu'elle active, le facteur $Z(\hat{\Lambda})$ étant commun à toutes les valeurs.

# Remarque

Ce jeu de traits reste binaire et ne dépend que de la traduction $y$, sans conditionnement sur le contexte. Dans le cadre conditionnel d'un [[Modèle log-linéaire conditionnel]], les traits prennent la forme $f_j(x, y)$ et peuvent dépendre à la fois de l'observation $x$ et de l'étiquette $y$, par exemple pour repérer qu'une traduction donnée suit un mot donné.

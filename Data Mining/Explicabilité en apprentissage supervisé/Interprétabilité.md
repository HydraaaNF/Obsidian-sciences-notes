#dmv-xai

# Définition

Un modèle est **interprétable** si « the rationale behind its answers can be understood by humans » : le raisonnement qui conduit des entrées à la réponse est compréhensible par un humain.

# Remarque

Une définition opératoire resserre cette exigence autour de trois critères : « A model can be said to be interpretable if, within a *given time limit*, the level of expertise of the user allows them to understand the model through its *representation*. »

- une **limite de temps** : la compréhension doit être atteinte dans un temps borné
- le **niveau d'expertise de l'utilisateur** : une même représentation n'est pas également lisible par tous les utilisateurs
- la **représentation** du modèle : c'est la représentation, et non le modèle en soi, que l'utilisateur doit comprendre

L'interprétabilité dépend donc du couple formé par l'utilisateur et la représentation, autant que du modèle.

Cette exigence se lit directement sur certaines formes : les coefficients du [[Lien logistique comme modèle interprétable|modèle logistique]], les tests d'un arbre, les prototypes des [[Méthodes à base d'exemplaires]]. Le [[Neurone formel]] en donne l'unité de calcul, et les [[Architectures et représentations des réseaux]] montrent où cette lecture se perd, quand les couches empilées n'exposent plus de coordonnées nommées.

Les attributs ne pèsent pas tous autant : le [[Graphique de dépendance partielle]] montre comment le modèle répond à chacun, et la [[Représentation interprétable]] retenue fixe ce qu'un utilisateur peut effectivement lire.

La position disciplinaire de cette exigence est décrite dans la [[Place de l'apprentissage automatique parmi les disciplines]], ses motivations dans les [[Motivations de l'explicabilité]], et les questions qu'elle laisse ouvertes dans les [[Questions ouvertes de l'explicabilité]].

# Interprétation

La complexité de certains modèles en fait des boîtes noires : la réponse est produite sans que le chemin qui y mène soit lisible, ce qui les fait ressembler à de la sorcellerie. Un réseau de neurones profond, par exemple, est une pile de couches dont seule l'entrée et la sortie sont accessibles, d'où l'image d'un classifieur enfermé dans une bulle de boîte noire.

Les familles de modèles se répartissent ainsi selon que leur représentation est lisible ou non.

| Modèles interprétables | Modèles boîtes noires |
|---|---|
| Fonctions linéaires | Réseaux de neurones |
| Arbres de décision et de régression | Méthodes d'ensemble (forêts aléatoires, gradient boosting) |
| Modèles à base de règles | Machines à vecteurs de support |
| Méthodes à base d'exemplaires | |
| Naïve Bayes | |
| RuleFit | |

Les deux familles s'opposent par un compromis : les modèles interprétables sont « Not always accurate but simpler », les modèles boîtes noires « Often accurate but not interpretable ». Le libellé de ce second constat s'écrit avec le mot *interpretable*.

# Propriétés

Un modèle interprétable est une boîte de verre : il fournit ses explications gratuitement, sans couche d'explication ajoutée. L'explication est alors lue directement sur la représentation du modèle, alors qu'un modèle boîte noire doit être doublé d'un traitement supplémentaire pour être expliqué, ce que décrit l'[[Explicabilité]].

# Exemple

Un modèle linéaire rend ses coefficients directement lisibles, chacun quantifiant l'effet d'une variable sur la prédiction :

$$y = -189.69 - 0.0002 \times cases + 2.39 \times score + 5.08 \times age$$

Un arbre de décision rend ses chemins directement lisibles : chaque branche est une conjonction de conditions qui mène à une feuille. Pour un passager de 14 ans, de sexe masculin, en troisième classe, l'arbre se lit comme quatre règles.

- Sexe féminin et troisième classe : RIP
- Sexe féminin et autre classe : Survived
- Sexe masculin et âge supérieur à 14 ans : RIP
- Sexe masculin et âge inférieur ou égal à 14 ans : Survived

Dans les deux cas, la représentation est elle-même l'explication : la forme du [[Modèle linéaire]] ou celle de l'[[Arbre de décision]] se lit sans outil intermédiaire. C'est cette lecture directe qui distingue l'interprétabilité de l'[[Explication]] produite après coup par une méthode dédiée, telle que celles que classe la [[Taxonomie des techniques d'explicabilité]].

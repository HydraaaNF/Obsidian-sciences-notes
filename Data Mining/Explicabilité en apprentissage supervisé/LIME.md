#dmv-xai

# Définition

**LIME** (*Local Interpretable Model-Agnostic Explanations*) calcule des **approximations linéaires agnostiques à la boîte noire** (*black-box agnostic*) de la prédiction d'un modèle. Agnostique signifie ici que la méthode ne suppose rien de la famille ni de la structure interne du modèle expliqué, dont elle n'exploite que les étiquettes attribuées aux instances qu'elle fabrique elle-même.

L'approximation est à la fois linéaire et locale : un substitut linéaire, donc un [[Modèle linéaire]], est appris au voisinage de l'instance expliquée, et ses coefficients forment une explication en attribution de variables. LIME est à ce titre un cas particulier de l'[[Explication locale]].

# Algorithme

Les étapes, dans l'ordre :

1. projeter l'instance dans un espace interprétable, où chaque coordonnée code la présence ($1$) ou l'absence ($0$) d'un composant directement compréhensible ;
2. échantillonner des voisins autour de l'instance cible dans cet espace ;
3. faire étiqueter ces voisins par la boîte noire, ce qui fournit un jeu d'étiquettes ;
4. apprendre un substitut linéaire sur ces étiquettes, chaque voisin étant pondéré par sa distance à la cible selon un noyau exponentiel ;
5. lire les coefficients du substitut comme l'explication.

L'espace interprétable dépend de la modalité des données, comme le détaillent les [[Formes d'explication selon la modalité des données]] et la [[Représentation interprétable]] : composants segmentés d'une image, mots d'un texte, présence ou absence de segments d'une série temporelle.

La pondération par proximité prend la forme d'un noyau exponentiel, où $x$ est l'instance expliquée, $z$ un voisin échantillonné, $D$ leur distance et $\sigma$ la largeur du noyau :

$$\pi_x(z) = \exp\left(-\frac{D(x,z)^2}{\sigma^2}\right)$$

Le substitut $g$ est alors obtenu par une régression locale pondérée, la perte étant augmentée d'un terme de complexité $\Omega$ qui favorise les substituts simples, $f$ désignant la boîte noire et $\mathcal{G}$ la famille des substituts linéaires :

$$g^{\star} = \arg\min_{g \in \mathcal{G}} \sum_{z} \pi_x(z) \left(f(z) - g(z)\right)^2 + \Omega(g)$$

# Interprétation

- chaque coefficient du substitut chiffre l'attribution d'un élément interprétable à la prédiction de l'instance ;
- l'explication porte sur cette prédiction seule et ne décrit pas le modèle entier ;
- l'utilisateur lit les éléments qui pèsent sur la décision dans un vocabulaire qui lui est accessible, et non dans celui du signal brut.

# Exemple

**Message d'un groupe de discussion.** Un message est classé *atheism* avec la probabilité $0{,}59$ contre $0{,}41$ pour *christian*. Les éléments interprétables retenus dans le message sont `edu` dans l'adresse électronique, `NNTP Posting Host` et le verbe `have`, et leurs contributions à la prédiction *atheism* décroissent ainsi :

```chart
type: bar
labels: ["Posting", "Host", "NNTP", "edu", "have"]
series:
  - title: Contribution à la prédiction atheism
    data: [0.16, 0.13, 0.10, 0.05, 0.03]
```

**Image.** Pour une photographie de grenouille, la boîte noire attribue à la classe *tree frog* la probabilité $0{,}54$. Trois instances perturbées, tirées dans le voisinage de l'image, reçoivent des probabilités très dispersées :

| Instance | $\mathbb{P}(\text{tree frog})$ |
|---|---:|
| instance perturbée 1 | $0{,}85$ |
| instance perturbée 2 | $0{,}00001$ |
| instance perturbée 3 | $0{,}52$ |

La régression localement pondérée ajustée sur ces instances fournit l'explication : les coefficients de la fonction linéaire se lisent sur les composants interprétables de l'image.

# Remarque

- L'approximation vaut au voisinage de l'instance expliquée : rien ne garantit que le substitut décrive la boîte noire ailleurs, et le caractère local est une contrainte de validité.
- Le voisinage dépend du tirage des échantillons et de la largeur du noyau : un noyau étroit concentre l'explication sur les alentours immédiats, un noyau large fait entrer des instances éloignées.
- L'échantillonnage étant aléatoire, deux tirages donnent deux voisinages et donc des coefficients qui peuvent varier d'une exécution à l'autre.
- Le substitut étant linéaire, il additionne les contributions des éléments interprétables et ne représente pas d'interaction entre eux.
- L'agnosticisme a un prix : la méthode vaut pour n'importe quel modèle, mais n'éclaire rien du mécanisme interne de celui-ci.
- « Black-box agnostic » et « model-agnostic » désignent la même propriété sous deux noms : l'agnosticisme porte sur la boîte noire, non sur une famille de modèles.
- La [[Représentation interprétable]] conditionne la lecture du résultat : des éléments que l'utilisateur ne comprend pas rendent l'explication inutilisable.
- D'autres méthodes d'attribution de variables existent, fondées sur les gradients ou sur la théorie des jeux, cette dernière menant à la [[Valeur de Shapley]] et à [[SHAP]].
- La fidélité du substitut s'évalue avec les [[Critères et métriques d'évaluation d'une explication]].
- La méthode s'oppose aux attributions obtenues par rétropropagation, voir les [[Méthodes d'attribution par gradients]].
- Une règle délimitant une région de l'instance est une autre forme locale, voir les [[Règles locales d'explication]].

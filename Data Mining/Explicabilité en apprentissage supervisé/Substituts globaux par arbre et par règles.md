#dmv-xai

# Définition

Un **substitut global** est un modèle interprétable appris non sur la vérité terrain mais sur les entrées et les sorties de la boîte noire, afin d'approximer celle-ci sur tout son domaine. C'est le substitut, et non la boîte noire, que l'utilisateur lit ensuite : il porte à lui seul l'[[Explication globale]].

Deux formes de substitut sont employées.

- l'**arbre de décision substitut** : la boîte noire est approximée par un [[Arbre de décision]], approche illustrée par Trepan, qui extrait un arbre à partir du réseau entraîné
- l'**ensemble de règles if-then** : des règles apprises par fouille d'itemsets, approche illustrée par BETA, de la famille des [[Règles, listes et ensembles de décision]]

# Modèle

L'ingénierie inverse se fait en deux étages : la boîte noire est d'abord apprise sur des données étiquetées, puis reprise comme source d'étiquettes pour le substitut.

```mermaid
flowchart LR
    A["Données étiquetées"] --> B["Phase d'apprentissage"]
    B --> C["Boîte noire"]
    C --> D["Données étiquetées par la boîte noire"]
    D --> E["Phase d'apprentissage du substitut"]
    E --> F["Classifieur interprétable"]
    F --> G["Utilisateur"]
```

Le cadre de BETA pose trois conventions.

- les règles sont restreintes à deux niveaux : une condition de premier niveau, puis des conditions de second niveau
- si deux règles contradictoires s'appliquent à un même exemple, celle de plus grande fidélité l'emporte
- les conditions, par exemple « sexe = féminin », sont obtenues par fouille de motifs

# Exemple

Une règle à deux niveaux, portant sur des données médicales.

Condition de premier niveau : Age > 50 et Gender = Male.

| conditions de second niveau | conclusion |
|---|---|
| Past-Depression = Yes, Insomnia = No, Melancholy = No | Healthy |
| Past-Depression = Yes, Insomnia = No, Melancholy = Yes | Depressed |

Les deux branches ne diffèrent que par Melancholy et concluent à deux classes opposées : la valeur de cette seule condition suffit à faire basculer la prédiction.

# Algorithme

La sélection de l'ensemble de règles $R$ est formulée comme un problème d'optimisation sur un espace de recherche de conditions.

$$\arg\max_{R \subseteq ND \times DL \times C} \sum_{i=1}^{5} \lambda_i f_i(R)$$

L'ensemble retenu est soumis à trois contraintes de taille.

- $size(R) \le \epsilon_1$
- $max\_width(R) \le \epsilon_2$
- $numdsets(R) \le \epsilon_3$

Les cinq fonctions $f_i$ agrègent les critères ; quatre d'entre elles sont adossées à une borne.

$$f_1(R) = P_{\max} - \mathrm{numpreds}(R)$$

où $P_{\max} = 2 \cdot W_{\max} \cdot |ND| \cdot |DL|$.

$$f_2(R) = O_{\max} - \mathrm{featureoverlap}(R)$$

où $O_{\max} = W_{\max} \cdot |ND| \cdot |DL|$.

$$f_3(R) = O'_{\max} - \mathrm{ruleoverlap}(R)$$

où $O'_{\max} = N \times (|ND| \cdot |DL|)^2$.

$$f_4(R) = \mathrm{cover}(R)$$

$$f_5(R) = F_{\max} - \mathrm{disagreement}(R)$$

où $F_{\max} = N \cdot |ND| \cdot |DL|$.

# Propriétés

Chaque terme mesure une grandeur distincte de l'ensemble de règles.

- $\mathrm{numpreds}(R)$ : nombre de prédicats portés par les règles de $R$, rapporté à $P_{\max}$
- $\mathrm{featureoverlap}(R)$ : chevauchement des variables entre règles, rapporté à $O_{\max}$
- $\mathrm{ruleoverlap}(R)$ : chevauchement des règles entre elles, rapporté à $O'_{\max}$
- $\mathrm{cover}(R)$ : couverture, seule grandeur sans borne associée
- $\mathrm{disagreement}(R)$ : désaccord entre les prédictions de $R$ et celles de la boîte noire, rapporté à $F_{\max}$

Quatre des cinq fonctions se lisent comme des pénalités, comptées à rebours depuis leur borne ; seule $f_4$ est un gain. Le maximum de l'objectif s'obtient donc en couvrant beaucoup, avec peu de prédicats, peu de recouvrement et peu de désaccord.

# Interprétation

Le problème d'optimisation poursuit trois objectifs simultanés.

- maximiser la fidélité et la couverture
- minimiser le nombre de règles, le recouvrement des variables et la complexité
- sous les contraintes du nombre de règles, de la largeur maximale et du nombre de conditions de premier niveau

Les trois contraintes plafonnent une à une les trois quantités correspondantes : $size$ pour le nombre de règles, $max\_width$ pour la largeur, $numdsets$ pour le nombre de conditions de premier niveau. La fidélité est portée par le désaccord pénalisé en $f_5$, la couverture par le gain $f_4$.

Un substitut reste une approximation : il ne rend compte du modèle opaque que dans la mesure où son accord avec lui est élevé et où les régions qu'il décrit sont effectivement couvertes. Ces deux quantités se mesurent séparément, et rien ne garantit qu'un substitut lisible soit aussi un substitut fidèle. Contrairement à une [[Explication locale]], qui justifie la sortie d'une instance, le substitut est appris une fois pour tout le domaine et se lit comme un modèle à part entière : sa lisibilité est celle d'un [[Arbre de décision]] ou d'un jeu de règles, bornée par la taille des objets que l'utilisateur accepte de parcourir.

# Remarque

- Une borne de comptage s'écrit une seule fois : $P_{\max} = 2 \cdot W_{\max} \cdot |ND| \cdot |DL|$. La chaîne $P_{\max} = P_{\max} = \ldots$ est une redondance mal formée, mais elle énonce bien cette valeur, celle que reprend $f_1$.
- Les bornes de degré ne sont pas homogènes : $O_{\max}$ et $F_{\max}$ ont la même forme mais l'une est facteur de $W_{\max}$ et l'autre de $N$, tandis que $O'_{\max}$ est la seule borne quadratique.
- Un même ensemble doit garder la même graphie d'un terme à l'autre : la contrainte et les cinq fonctions nomment les mêmes objets, et l'écriture d'un ensemble ne doit pas changer entre les deux.
- La restriction à deux niveaux borne l'expressivité du substitut : un comportement qui exigerait un troisième niveau de conditions n'est pas représentable, quelle que soit la fidélité atteinte.
- Le choix de $R$ est un problème combinatoire sur $ND \times DL \times C$, et les cinq critères sont pondérés par des coefficients $\lambda_i$ qu'il faut fixer : deux jeux de coefficients différents produisent deux substituts différents sur la même boîte noire.
- Une règle locale restreint la même forme à une instance et à son voisinage, voir les [[Règles locales d'explication]].

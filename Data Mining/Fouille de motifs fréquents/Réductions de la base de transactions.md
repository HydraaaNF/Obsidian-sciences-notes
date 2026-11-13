#dmv-frequent_itemsets_mining

# Définition

Une **base conditionnelle** est la [[Items, itemsets et base de transactions|base de transactions]] réduite aux items et aux transactions utiles à l'exploration des niveaux plus profonds de la fouille.

La réduction écarte les items qui ne peuvent appartenir à aucun [[Itemset fréquent|itemset fréquent]], puis réunit les transactions identiques en une seule entrée affectée de leur nombre d'occurrences.

# Algorithme

Les réductions s'appliquent à la base, avant toute construction de structure de recherche.

1. **Filtrage par items infréquents et items universellement inclus.**

   Chaque transaction est amputée de ses items de [[Support d'un itemset|support]] inférieur au seuil $\theta$, et de ses items présents dans toutes les transactions.

2. **Unification des transactions identiques.**

   Les transactions devenues identiques après le filtrage sont regroupées en une seule entrée, accompagnée du nombre de transactions qu'elle représente.

L'unification se fait en temps linéaire sur la base filtrée.

Le résultat est une base de taille réduite, sur laquelle se construit ensuite l'[[Arbre FP|arbre de préfixes]].

# Propriétés

- Le filtrage retire les items infréquents et les items universellement inclus.
- Les transactions identiques sont réunies automatiquement après le filtrage, en temps linéaire.
- Sur la base réduite, l'[[Arbre FP|arbre de préfixes]] coûte $O(|D| \log |D|)$ en temps, où $|D|$ est la taille de la base.

# Exemple

Base initiale de six transactions, avec le seuil $\theta = 3$ :

- $\{1, 3, 5\}$
- $\{1, 3, 5\}$
- $\{1, 3, 5\}$
- $\{1, 2, 5, 6\}$
- $\{1, 4, 6\}$
- $\{1, 2, 6\}$

L'item $1$ figure dans les six transactions, donc dans toutes : il est universellement inclus et disparaît. L'item $2$ a un support de $2$ et l'item $4$ un support de $1$, tous deux sous le seuil $\theta = 3$ : ils disparaissent aussi. Les items $3$, $5$ et $6$, de supports respectifs $3$, $4$ et $3$, sont conservés.

Base filtrée :

- $\{3, 5\}$
- $\{3, 5\}$
- $\{3, 5\}$
- $\{5, 6\}$
- $\{6\}$
- $\{6\}$

Les trois premières transactions sont identiques, les deux dernières également ; l'unification les regroupe.

Base réduite :

- $\{3, 5\}$ pour trois transactions
- $\{5, 6\}$ pour une transaction
- $\{6\}$ pour deux transactions

# Remarque

Le filtrage des items infréquents est sans perte pour la recherche des itemsets fréquents : aucun itemset fréquent ne contient un item dont le support est inférieur au seuil, puisque le support d'un sur-ensemble ne dépasse jamais celui de ses parties ([[Propriété d'anti-monotonie du support]]).

Un item présent dans toutes les transactions ne sépare aucune transaction des autres : il accompagne chaque itemset sans en modifier l'ordre de fréquence. Il peut donc être mis de côté, puis réintroduit dans les itemsets retenus.

L'unification ne perd aucune information de comptage : le nombre de transactions regroupées est conservé dans la base réduite, et c'est lui qui alimente les compteurs de l'[[Arbre FP]]. Les transactions identiques y comptent pour leur multiplicité, ce qui rend la base d'autant plus compacte que la base d'origine est redondante.

Ces réductions préparent le terrain de la même façon que le [[Prétraitement de la base pour FP-growth|prétraitement de la base pour FP-growth]], et la base réduite est celle que reçoit l'exploration descendante de l'[[Algorithme LCM]] à chaque niveau plus profond de la recherche.

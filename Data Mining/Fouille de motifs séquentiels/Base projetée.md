#dmv-sequence_mining

# Définition

Soit $\alpha$ un préfixe. La **base projetée** de $\alpha$, ou base de données projetée, rassemble les projections sur $\alpha$ des séquences de la [[Base de séquences|base de séquences]] qui [[Inclusion de sous-séquence|contiennent]] ce préfixe.

Pour chaque séquence retenue, la projection est la partie de la séquence située après la fin de l'occurrence de $\alpha$ : c'est le [[Suffixe d'une séquence|suffixe]] qui reste une fois le préfixe consommé.

Quand l'occurrence de $\alpha$ s'achève à l'intérieur d'un itemset, les items consommés de cet itemset sont retirés et un marqueur $\_$ est placé en tête de l'itemset restant, pour rappeler que la coupe s'est faite au milieu de l'itemset.

# Exemple

Base de quatre séquences et projections sur le préfixe $\langle a\rangle$ :

| Id_seq | Séquence | Projection sur $\langle a\rangle$ |
|---|---|---|
| 10 | $\langle a(abc)(ac)d(cf)\rangle$ | $\langle(abc)(ac)d(cf)\rangle$ |
| 20 | $\langle(ad)c(bc)(ae)\rangle$ | $\langle(\_d)c(bc)(ae)\rangle$ |
| 30 | $\langle(ef)(ab)(df)cb\rangle$ | $\langle(\_b)(df)cb\rangle$ |
| 40 | $\langle eg(af)cbc\rangle$ | $\langle(\_f)cbc\rangle$ |

Les séquences 20, 30 et 40 voient le préfixe s'achever dans un itemset qui contient d'autres items : l'itemset coupé survit sous la forme $\langle(\_d)\rangle$, $\langle(\_b)\rangle$ et $\langle(\_f)\rangle$. La séquence 10 s'arrête sur un itemset entièrement consommé, qui disparaît sans laisser de trace.

Base projetée du préfixe $\langle acc\rangle$ :

| Id_seq | Projection |
|---|---|
| 10 | $\langle d(cf)\rangle$ |
| 20 | $\langle(ae)\rangle$ |
| 30 | $\langle b\rangle$ |
| 40 | $\langle\rangle$ |

La projection de la séquence 40 est vide : le préfixe y consomme toute la séquence.

Le résultat final de l'algorithme PrefixSpan sur la base de séquences, par ordre croissant de longueur (la base projetée de $\langle acc\rangle$ n'est qu'une étape intermédiaire de l'énumération) :

- $\langle a\rangle$
- $\langle b\rangle$
- $\langle c\rangle$
- $\langle a\ b\rangle$
- $\langle a\ c\rangle$
- $\langle c\ c\rangle$
- $\langle a\ c\ c\rangle$

# Remarque

La base projetée guide l'exploration de l'[[Espace de recherche des motifs séquentiels|espace de recherche]] : le préfixe $\langle a\rangle$ délimite le sous-ensemble des motifs qui commencent par $a$, et sa base projetée ne contient plus que les suites d'itemsets capables de prolonger ce préfixe. Le support d'une extension de $\alpha$ se calcule directement sur cette base, ce qui restreint le comptage aux seules séquences encore candidates.

Chaque niveau de récursion produit une base projetée plus petite que la précédente. C'est cette décroissance que l'[[Algorithme PrefixSpan]] exploite pour énumérer les [[Motif séquentiel|motifs séquentiels]] sans générer de candidats.

Construire la base projetée revient à recopier des suffixes de séquences, ce qui constitue l'étape la plus coûteuse de l'algorithme : la [[Pseudo-projection]] remplace cette copie par un pointeur sur la séquence et un offset identifiant le suffixe.

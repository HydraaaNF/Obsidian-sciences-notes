#dmv-sequence_mining

# Définition

SPADE (Sequential Pattern Discovery using Equivalent classes) est un algorithme de fouille de [[Motif séquentiel|motifs séquentiels]] fondé sur le [[Format vertical des transactions|format de données vertical]] : la [[Base de séquences|base de séquences]] est convertie en une entrée par item, chaque item portant la liste de ses occurrences, repérées par un couple (SID, EID).

Il résout le même [[Énoncé du problème de fouille de motifs séquentiels|problème de fouille]] que l'[[Algorithme GSP]] : produire toutes les sous-séquences dont le [[Support d'un motif séquentiel|support]] atteint le seuil $minsup$. La différence porte sur le comptage : au lieu de balayer les séquences à chaque niveau de longueur, SPADE lit le support dans les listes d'occurrences.

# Algorithme

- parcourir la base et la convertir au format vertical : chaque item reçoit la liste de ses couples (SID, EID), le SID identifiant la séquence et l'EID la position de l'itemset dans cette séquence ;
- filtrer les 1-séquences non fréquentes, le support d'une 1-séquence étant le nombre de SID distincts de sa liste (avec $minsup=4$, les seules 1-séquences fréquentes sont $\langle b\rangle$ et $\langle c\rangle$) ;
- joindre des $k$-séquences qui partagent un SID et dont les EID suivent l'ordre séquentiel, ce qui engendre les $(k+1)$-séquences candidates ;
- filtrer les $(k+1)$-séquences non fréquentes, en comptant à nouveau les SID distincts ;
- répéter la jointure et le filtrage jusqu'à ce qu'aucune séquence ne puisse plus être engendrée.

Trois réductions de l'espace mémoire accompagnent la jointure :

- ne joindre que deux $k$-séquences qui ont toutes leurs sous-séquences en commun sauf le dernier élément, ce qui reprend l'amélioration lexicographique de la [[Génération des candidats par apriori-gen|génération des candidats par itemsets]] ;
- ne stocker qu'un seul EID par occurrence, celui du dernier élément de la séquence ;
- décomposer le treillis en classes de séquences et traiter une classe à la fois.

# Exemple

Base de séquences de cinq séquences :

| SID | Séquence |
| :-: | :- |
| 1 | $\langle (bd)\ c\ b\ (ac)\rangle$ |
| 2 | $\langle (bf)\ (ce)\ b\ (fg)\rangle$ |
| 3 | $\langle (ah)\ (bf)\ a\ b\ f\rangle$ |
| 4 | $\langle (be)\ (ce)\ d\rangle$ |
| 5 | $\langle a\ (bd)\ b\ c\ b\ (ade)\rangle$ |

Conversion au format vertical, une entrée par item :

| Item | Couples (SID, EID) |
| :-: | :- |
| $a$ | $(1,4)$, $(3,1)$, $(3,3)$, $(5,1)$, $(5,6)$ |
| $b$ | $(1,1)$, $(1,3)$, $(2,1)$, $(2,3)$, $(3,2)$, $(3,4)$, $(4,1)$, $(5,2)$, $(5,3)$, $(5,5)$ |
| $c$ | $(1,2)$, $(1,4)$, $(2,2)$, $(4,2)$, $(5,4)$ |
| $d$ | $(1,1)$, $(4,3)$, $(5,2)$, $(5,6)$ |
| $e$ | $(2,2)$, $(4,1)$, $(4,2)$, $(5,6)$ |
| $f$ | $(2,1)$, $(2,4)$, $(3,2)$, $(3,5)$ |
| $g$ | $(2,4)$ |
| $h$ | $(3,1)$ |

Avec $minsup=4$, le filtre des 1-séquences ne retient que $\langle b\rangle$ et $\langle c\rangle$ : les SID de $b$ sont $1, 2, 3, 4, 5$ et ceux de $c$ sont $1, 2, 4, 5$, tandis que les items $a$, $d$, $e$, $f$, $g$ et $h$ restent sous le seuil.

La jointure de $\langle b\rangle$ et de $\langle c\rangle$ s'effectue dans les deux ordres. Pour $\langle b\ c\rangle$, on garde les couples où l'occurrence de $b$ précède celle de $c$ dans la même séquence :

| SID | EID de $b$ | EID de $c$ |
| :-: | :-: | :-: |
| 1 | 1 | 2 |
| 1 | 1 | 4 |
| 1 | 3 | 4 |
| 2 | 1 | 2 |
| 4 | 1 | 2 |
| 5 | 2 | 4 |
| 5 | 3 | 4 |

Pour $\langle c\ b\rangle$, on garde l'ordre inverse :

| SID | EID de $c$ | EID de $b$ |
| :-: | :-: | :-: |
| 1 | 2 | 3 |
| 2 | 2 | 3 |
| 5 | 4 | 5 |

Chaque ligne jointe est une occurrence de la séquence candidate ; le support se lit ensuite en comptant les SID distincts présents dans la table.

# Remarque

Dans la table verticale, l'EID d'un item est celui de l'itemset qui le contient : deux items d'un même itemset portent donc le même EID, et c'est ce recoupement avec les séquences qui fixe les positions. Les couples $(\text{SID}, \text{EID})$ de la table sont ceux que donne cette règle appliquée aux séquences de l'exemple ; toute numérotation EID qui ne la respecte pas ne décrit pas les mêmes positions.

Le filtre des 1-séquences et celui des $(k+1)$-séquences reposent sur la même [[Anti-monotonie du support des motifs séquentiels|propriété d'anti-monotonie du support]] que dans l'[[Algorithme GSP]] : une séquence non fréquente interdit toutes ses sur-séquences, ce qui permet d'élaguer une branche sans compter les candidats qu'elle contient.

La décomposition en classes de séquences est ce qui donne son nom à l'algorithme : les séquences sont rangées dans des classes d'équivalence, comme les itemsets le sont dans le [[Classes d'équivalence des itemsets|treillis des itemsets]], et la fouille progresse classe par classe plutôt que sur le treillis entier.

#dmv-sequence_mining

# Exemple

**Longueur de deux séquences.** Une $k$-séquence est une séquence de longueur $k$, la longueur se comptant en items et un itemset de $m$ items pesant $m$, comme le fixe le [[Vocabulaire des motifs séquentiels|vocabulaire des motifs séquentiels]]. Quelles sont les longueurs des deux séquences suivantes :

$$\langle(a)\ (c)\ (d\ e)\rangle$$

$$\langle(a)\ (c)\ (d)\ (z)\ (y)\rangle$$

**Tests d'inclusion.** Soit la séquence

$$S_1 = \langle(10)\ (20\ 30)\ (40)\ (20)\rangle$$

Les deux inclusions suivantes sont-elles vérifiées :

$$\langle(20)\ (40)\rangle \subseteq S_1$$

$$\langle(20)\ (30)\rangle \subseteq S_1$$

**Supports de quatre motifs.** Une base de quatre séquences est indexée par quatre dates $d_1$, $d_2$, $d_3$, $d_4$ ; un tiret signale l'absence d'événement à cette date.

| Séquence | $d_1$ | $d_2$ | $d_3$ | $d_4$ |
| :-: | :-: | :-: | :-: | :-: |
| $S_1$ | abc | bde | abf | ad |
| $S_2$ | abc | abc | - | bcf |
| $S_3$ | bce | - | adf | abc |
| $S_4$ | acf | bd | abf | e |

Calculer la valeur de support des quatre motifs séquentiels suivants :

$$\langle(a)\ (bd)\ (a)\rangle$$

$$\langle(b)\ (b)\ (f)\rangle$$

$$\langle(b)\ (d)\ (f)\rangle$$

$$\langle(cf)\ (b)\rangle$$

**Jointure de deux $k$-séquences selon SPADE.** Avec $minsup = 3$, joindre les deux séquences dont les listes d'identifiants sont données ci-dessous, une fois en $\langle d\ e\rangle$ et une fois en $\langle e\ d\rangle$, puis décider du caractère fréquent du résultat.

Séquence $d$ :

| SID | EID |
| :-: | :-: |
| 1 | 2 |
| 2 | 2 |
| 3 | 4 |
| 3 | 5 |
| 4 | 5 |
| 5 | 2 |
| 5 | 6 |
| 6 | 1 |
| 6 | 5 |

Liste de la séquence $e$ :

| SID | EID |
| :-: | :-: |
| 1 | 2 |
| 2 | 3 |
| 3 | 4 |
| 3 | 6 |
| 4 | 3 |
| 4 | 6 |
| 5 | 6 |
| 6 | 5 |
| 6 | 7 |

**Application de PrefixSpan.** Avec $minsup = 4$ en support absolu, soit un support relatif $4/4 = 1$, c'est-à-dire $100\,\%$, appliquer [[Algorithme PrefixSpan|PrefixSpan]] à la base suivante et donner les motifs séquentiels fréquents.

| Id_seq | Séquence |
| :-: | :-: |
| 10 | $\langle a(abc)(ac)d(cf)\rangle$ |
| 20 | $\langle(ad)c(bc)(ae)\rangle$ |
| 30 | $\langle(ef)(ab)(df)ccb\rangle$ |
| 40 | $\langle eg(af)cbc\rangle$ |

**Supports sous contrainte d'écart temporel.** La [[Contrainte d'écart temporel|contrainte d'écart temporel]] vaut ici $[0,1]$.

| Séquence / date | $t=1$ | $t=2$ | $t=3$ | $t=4$ | $t=5$ | $t=6$ |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| $S_1$ | abc | b | de | af | b | ad |
| $S_2$ | abc | bc | a | bcf | | |
| $S_3$ | bce | adf | e | abc | f | |
| $S_4$ | acf | bd | abf | e | | |

Calculer les valeurs de support des quatre motifs suivants :

$$\langle a\ (bd)\ a\rangle$$

$$\langle b\ b\ f\rangle$$

$$\langle b\ d\ f\rangle$$

$$\langle(cf)\ b\rangle$$

# Remarque

**Longueurs.** La longueur d'une séquence est le nombre d'items qu'elle contient, un itemset de $m$ items comptant pour $m$ et non pour un :

- $\langle(a)\ (c)\ (d\ e)\rangle$ contient les items a, c, d, e, soit $1+1+2 = 4$ items : c'est une 4-séquence ;
- $\langle(a)\ (c)\ (d)\ (z)\ (y)\rangle$ contient les items a, c, d, z, y, soit $5$ items : c'est une 5-séquence.

L'itemset $(d\ e)$ pèse donc deux unités, alors qu'il ne forme qu'un seul élément de la séquence.

**Inclusion.** Une séquence $S_1$ est une [[Inclusion de sous-séquence|sous-séquence]] d'une séquence $S_2$ s'il existe des indices $1 \le i_1 < i_2 < \dots < i_n \le m$ tels que chaque itemset de $S_1$ soit inclus dans l'itemset de $S_2$ de même rang, les indices étant strictement croissants.

- Pour $\langle(20)\ (40)\rangle$ : l'itemset $(20)$ est inclus dans $(20\ 30)$, de rang 2, et $(40)$ dans $(40)$, de rang 3 ; les rangs $2 < 3$ conviennent, l'inclusion est vérifiée.
- Pour $\langle(20)\ (30)\rangle$ : l'itemset $(20)$ se place au rang 2 ou au rang 4, et $(30)$ uniquement au rang 2, à l'intérieur de $(20\ 30)$ ; il faudrait un rang pour $(30)$ postérieur au rang de $(20)$, ce qui est impossible, l'inclusion n'est pas vérifiée.

La différence tient à la simultanéité : deux items tirés du même itemset ne peuvent pas se suivre. En revanche l'itemset unique $\langle(20\ 30)\rangle$ est bien une sous-séquence de $S_1$, au rang 2, et non de la seconde séquence, où la position de $(20)$ ne peut pas être antérieure à celle de $(30)$.

**Supports.** Le [[Support d'un motif séquentiel|support]] d'un motif est la proportion des séquences de la base qui le contiennent comme sous-séquence. Chaque séquence est lue colonne par colonne, dans l'ordre des dates.

- $\langle(a)\ (bd)\ (a)\rangle$ : $S_1$ convient, avec a en $d_1$, l'itemset $(bd)$ en $d_2$ et a en $d_3$ ; $S_2$ ne contient aucun d ; $S_3$ a un a en $d_3$ puis en $d_4$, mais aucun itemset ne réunit b et d ; $S_4$ convient, avec a en $d_1$, $(bd)$ en $d_2$ et a en $d_3$. Le support vaut $2/4 = 0{,}5$.
- $\langle(b)\ (b)\ (f)\rangle$ : $S_1$ fournit b en $d_1$, b en $d_2$ et f en $d_3$ ; $S_2$ fournit b en $d_1$, b en $d_2$ et f en $d_4$ ; $S_3$ a ses deux b en $d_1$ et $d_4$, mais son seul f est en $d_3$, antérieur au second b ; $S_4$ a ses deux b en $d_2$ et $d_3$ sans f postérieur, le sien étant en $d_1$. Le support vaut $2/4 = 0{,}5$.
- $\langle(b)\ (d)\ (f)\rangle$ : $S_1$ fournit b en $d_1$, d en $d_2$ puis f en $d_3$ ; $S_2$ ne contient aucun d ; $S_3$ a b en $d_1$ et d en $d_3$, mais le f de cet itemset est simultané à d et non postérieur, et aucun f ne vient ensuite ; $S_4$ n'a aucun d postérieur à un b, son d de $d_2$ partageant l'itemset de b. Le support vaut $1/4 = 0{,}25$.
- $\langle(cf)\ (b)\rangle$ : l'itemset $(cf)$ exige c et f simultanés ; $S_1$ n'a aucun itemset réunissant c et f, $S_2$ a bien c et f ensemble en $d_4$ mais aucun b ensuite, $S_3$ n'a jamais c et f ensemble ; seule $S_4$ convient, avec $(cf)$ en $d_1$ puis b en $d_2$. Le support vaut $1/4 = 0{,}25$.

**Jointure SPADE.** La [[Algorithme SPADE|jointure]] de deux listes d'identifiants produit une séquence de longueur $k+1$ : chaque couple (SID, EID) de la première liste s'apparie aux couples de la seconde liste de même SID dont l'EID est strictement supérieur. Pour limiter la place mémoire, le couple produit ne retient que la valeur du dernier élément. La séquence est fréquente lorsque le nombre de SID distincts atteint $minsup$.

Pour $\langle d\ e\rangle$, le dernier élément est le e :

| SID de $d$ | EID de $d$ | EID de $e$ supérieurs | couples produits |
| :-: | :-: | :-: | :-: |
| 1 | 2 | aucun (EID égal) | - |
| 2 | 2 | 3 | (2, 3) |
| 3 | 4 | 6 | (3, 6) |
| 3 | 5 | 6 | (3, 6) |
| 4 | 5 | 6 | (4, 6) |
| 5 | 2 | 6 | (5, 6) |
| 5 | 6 | aucun | - |
| 6 | 1 | 5 et 7 | (6, 5), (6, 7) |
| 6 | 5 | 7 | (6, 7) |

Les appariements sont au nombre de huit, mais deux couples sortent deux fois : $(3,6)$ provient des deux EID de $d$ du SID 3, et $(6,7)$ des deux EID de $d$ du SID 6, que l'EID du dernier élément ne distingue plus. La liste de $\langle d\ e\rangle$ est donc $(2,3)$, $(3,6)$, $(4,6)$, $(5,6)$, $(6,5)$, $(6,7)$ ; elle couvre les SID 2, 3, 4, 5 et 6, soit $5 \ge 3$ : la séquence est fréquente.

Pour $\langle e\ d\rangle$, le dernier élément est cette fois le d, et un couple de $e$ s'apparie aux couples de $d$ de même SID dont l'EID est strictement supérieur :

| SID de $e$ | EID de $e$ | EID de $d$ supérieurs | couples produits |
| :-: | :-: | :-: | :-: |
| 1 | 2 | aucun (EID égal) | - |
| 2 | 3 | aucun | - |
| 3 | 4 | 5 | (3, 5) |
| 3 | 6 | aucun | - |
| 4 | 3 | 5 | (4, 5) |
| 4 | 6 | aucun | - |
| 5 | 6 | aucun | - |
| 6 | 5 | aucun (EID égal) | - |
| 6 | 7 | aucun | - |

La liste de $\langle e\ d\rangle$ est $(3,5)$, $(4,5)$ ; elle ne couvre que les SID 3 et 4, soit $2 < 3$ : la séquence n'est pas fréquente et la branche est élaguée.

Le cas d'un EID égal, présent pour le SID 1, correspond à d et e simultanés : il engendrerait l'itemset unique $\langle(de)\rangle$, et non la séquence de deux itemsets.

**PrefixSpan.** Le support de chaque item, compté en nombre de séquences, élimine les items trop rares :

| item | séquences | support |
| :-: | :-: | :-: |
| a | 10, 20, 30, 40 | 4 |
| b | 10, 20, 30, 40 | 4 |
| c | 10, 20, 30, 40 | 4 |
| d | 10, 20, 30 | 3 |
| e | 20, 30, 40 | 3 |
| f | 10, 30, 40 | 3 |
| g | 40 | 1 |

Seuls a, b et c atteignent $minsup = 4$ ; les extensions qui les suivent se calculent sur la [[Base projetée|base projetée]] de chaque préfixe :

| préfixe | extension | séquences | support |
| :-: | :-: | :-: | :-: |
| $\langle a\rangle$ | a | 10, 20 | 2 |
| $\langle a\rangle$ | b | 10, 20, 30, 40 | 4 |
| $\langle a\rangle$ | c | 10, 20, 30, 40 | 4 |
| $\langle a\rangle$ | d | 10, 30 | 2 |
| $\langle a\rangle$ | e | 20 | 1 |
| $\langle a\rangle$ | f | 10, 30 | 2 |
| $\langle b\rangle$ | a | 10, 20 | 2 |
| $\langle b\rangle$ | b | 30 | 1 |
| $\langle b\rangle$ | c | 10, 30, 40 | 3 |
| $\langle b\rangle$ | d | 10, 30 | 2 |
| $\langle b\rangle$ | e | 20 | 1 |
| $\langle b\rangle$ | f | 10, 30 | 2 |
| $\langle c\rangle$ | a | 10, 20 | 2 |
| $\langle c\rangle$ | b | 20, 30, 40 | 3 |
| $\langle c\rangle$ | c | 10, 20, 30, 40 | 4 |
| $\langle c\rangle$ | d | 10 | 1 |
| $\langle c\rangle$ | e | 20 | 1 |
| $\langle c\rangle$ | f | 10 | 1 |

Les extensions fréquentes sont donc $\langle a\ b\rangle$, $\langle a\ c\rangle$ et $\langle c\ c\rangle$ ; aucune autre ne dépasse $3$ séquences, et g n'apparaît jamais après a, b ou c. En poursuivant sur ces préfixes :

- $\langle a\ b\rangle$ n'a aucune extension atteignant 4, la meilleure étant $\langle a\ b\ a\rangle$ et $\langle a\ b\ c\rangle$ avec 2 séquences ;
- $\langle a\ c\rangle$ s'étend en $\langle a\ c\ c\rangle$ avec 4 séquences, c apparaissant après le premier c dans chacune des quatre séquences ;
- $\langle c\ c\rangle$ n'a aucune extension atteignant 4, $\langle c\ c\ c\rangle$ et $\langle c\ c\ b\rangle$ ne dépassant pas une séquence ;
- $\langle a\ c\ c\rangle$ n'a aucune extension atteignant 4, $\langle a\ c\ c\ b\rangle$ n'étant portée que par la séquence 30.

Les motifs fréquents sont les préfixes de ces branches, soit

$$\langle a\rangle, \langle b\rangle, \langle c\rangle$$

$$\langle a\ b\rangle, \langle a\ c\rangle, \langle c\ c\rangle$$

$$\langle a\ c\ c\rangle$$

Les motifs maximaux ($\langle a\ b\rangle$, $\langle a\ c\ c\rangle$, $\langle b\rangle$, $\langle c\ c\rangle$) résument la sortie, tous les autres en étant des préfixes.

**Écart temporel.** L'écart se compte en unités de temps **sautées** entre deux itemsets consécutifs du motif, et non en différence de dates : deux itemsets réalisés aux dates $t$ et $t'$ présentent l'écart

$$\text{gap} = t' - t - 1$$

Un écart nul correspond donc à deux itemsets contigus, et l'intervalle $[0,1]$ autorise un saut d'une unité au plus, soit des itemsets séparés de une ou deux dates : deux itemsets consécutifs d'un motif se réalisent ainsi à deux dates $t$ et $t'$ telles que $1 \le t' - t \le 2$. Les dates des itemsets restent strictement croissantes : deux itemsets de même date formeraient un seul itemset.

- $\langle a\ (bd)\ a\rangle$ : seule $S_4$ réunit b et d dans un même itemset, en $t=2$ ; elle fournit a en $t=1$, $(bd)$ en $t=2$ et a en $t=3$, deux écarts nuls. $S_1$ a b en $t=1$ et d en $t=3$, jamais dans un même itemset ; $S_2$ et $S_3$ non plus. Le support vaut $1/4 = 0{,}25$.
- $\langle b\ b\ f\rangle$ : $S_1$ fournit b en $t=1$, b en $t=2$ et f en $t=4$, l'itemset de $t=3$ ne portant que de, soit un écart nul puis l'écart $1$ qui saute $t=3$ ; $S_2$ fournit b en $t=1$, b en $t=2$ et f en $t=4$, un écart nul puis l'écart $1$ de $t=2$ à $t=4$, qui saute la seule unité $t=3$ ; $S_3$ n'a que b en $t=1$ et $t=4$, séparés de trois dates, soit un écart de $2$, hors de l'intervalle ; $S_4$ a ses deux b en $t=2$ et $t=3$, mais son f de $t=3$ est simultané au second b et $t=4$ ne porte pas f. Le support vaut $2/4 = 0{,}5$.
- $\langle b\ d\ f\rangle$ : $S_1$ convient avec b en $t=2$, d en $t=3$ et f en $t=4$, deux écarts nuls, et convient aussi avec b en $t=1$, d en $t=3$ et f en $t=4$, soit un écart de $1$ puis un écart nul ; $S_2$ ne contient aucun d ; $S_3$ a b en $t=1$, d en $t=2$ puis f en $t=5$, séparés de trois dates, soit un écart de $2$ ; $S_4$ n'a aucun d postérieur à son b, son d de $t=2$ partageant l'itemset de b. Le support vaut $1/4 = 0{,}25$.
- $\langle(cf)\ b\rangle$ : $S_4$ fournit $(cf)$ en $t=1$ et b en $t=2$, écart nul ; $S_2$ a bien c et f ensemble en $t=4$ mais aucun b ensuite ; $S_1$ et $S_3$ n'ont aucun itemset réunissant c et f. Le support vaut $1/4 = 0{,}25$.

La contrainte d'écart temporel abaisse donc les supports : sans elle, sur cette même table, $\langle b\ b\ f\rangle$ serait supporté par $S_1$, $S_2$ et $S_3$, soit $3/4$, et $\langle b\ d\ f\rangle$ par $S_1$ et $S_3$, soit $2/4$ ; l'écart maximal les ramène à $2/4$ et $1/4$.

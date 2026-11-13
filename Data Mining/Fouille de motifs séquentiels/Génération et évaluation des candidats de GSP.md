#dmv-sequence_mining

# Algorithme

À chaque niveau $k$, l'[[Algorithme GSP]] alterne deux opérations : engendrer les candidats de longueur $k+1$ à partir des motifs fréquents de longueur $k$, puis évaluer ces candidats en balayant la base pour compter leur [[Support d'un motif séquentiel|support]].

L'engendrement se fait par self-join de deux séquences fréquentes $s_1$ et $s_2$ de longueur $k$, noté $s_1 + s_2$. Les deux séquences ne s'assemblent que si le suffixe de $s_1$ privé de son premier item égale le préfixe de $s_2$ privé de son dernier item : le recouvrement porte alors sur $k-1$ items.

- retirer le premier item de $s_1$ et le dernier item de $s_2$ ;
- lorsque les deux séquences restantes coïncident, engendrer le candidat formé de $s_1$ suivi de l'item retiré de $s_2$.

Le candidat produit a la longueur $k+1$. L'item ajouté forme un nouvel élément (extension de séquence) ou rejoint le dernier élément de $s_1$ (extension d'itemset) : ce sont les deux façons d'[[Extensions d'une séquence|étendre une séquence]], et les deux formes ne s'excluent pas, deux motifs d'un seul item $\langle a\rangle$ et $\langle b\rangle$ engendrant à la fois $\langle(a)(b)\rangle$ et $\langle(ab)\rangle$. Lorsque le dernier élément de $s_2$ regroupe plusieurs items, seule la fusion conserve cet élément entier dans le candidat.

Au niveau 1, les candidats sont les items fréquents de la base, notés $\langle a\rangle$, $\langle b\rangle$. Au niveau 2, le self-join des motifs fréquents de longueur 1 produit les séquences $\langle(A)(A)\rangle$, $\langle(A)(B)\rangle$ et $\langle(A\ B)\rangle$.

# Exemple

L'énumération se déroule sur une base de 5 séquences décrites par 8 items, avec $minsup = 2$ :

| Identifiant | Séquence |
|:--|:--|
| 1 | $\langle (bd)(c)(b)(ac)\rangle$ |
| 2 | $\langle (bf)(ce)(b)(fg)\rangle$ |
| 3 | $\langle (ah)(bf)(a)(b)(f)\rangle$ |
| 4 | $\langle (be)(ce)(d)\rangle$ |
| 5 | $\langle (a)(bd)(b)(c)(b)(ade)\rangle$ |

Les itemsets sont écrits entre parenthèses, y compris les singletons : $\langle (bd)(c)(b)(ac)\rangle$ se lit comme la suite ordonnée des itemsets $\{b, d\}$, $\{c\}$, $\{b\}$, $\{a, c\}$.

Deux exemples de self-join, où le retrait du premier item de $s_1$ et du dernier item de $s_2$ laisse la même séquence $\langle (B)(C)\rangle$ :

$$\langle (A\ B)(C)\rangle + \langle (B)(C\ D)\rangle = \langle (A\ B)(C\ D)\rangle$$

$$\langle (A\ B)(C)\rangle + \langle (B)(C)(E)\rangle = \langle (A\ B)(C)(E)\rangle$$

Dans le premier cas, $D$ rejoint l'itemset $\{C\}$ du dernier élément et donne une extension d'itemset ; dans le second, $E$, seul dans le dernier élément de $s_2$, ouvre un nouvel élément et donne une extension de séquence.

Sur la base ci-dessus, seuls 6 des 8 items sont fréquents : les motifs de longueur 1 retenus sont $\langle a\rangle$, $\langle b\rangle$, $\langle c\rangle$, $\langle d\rangle$, $\langle e\rangle$, $\langle f\rangle$. Leur self-join produit deux familles de candidats de longueur 2, selon que l'item ajouté ouvre un nouvel élément ou rejoint le dernier itemset :

- les extensions de séquence, une par couple ordonné d'items, soit $\langle(a)(a)\rangle$, $\langle(a)(b)\rangle$, $\dots$, $\langle(f)(f)\rangle$ ;
- les extensions d'itemset, une par paire d'items distincts, soit $\langle(ab)\rangle$, $\langle(ac)\rangle$, $\dots$, $\langle(ef)\rangle$.

Cela donne $6 \times 6 = 36$ candidats de la première famille et $6 \times 5/2 = 15$ de la seconde, soit 51 séquences de 2 items.

# Propriétés

Sans [[Anti-monotonie du support des motifs séquentiels|propriété d'anti-monotonie]], le nombre de candidats de longueur 2 sur $n$ items se décompte par famille :

- $n^2$ extensions de séquence, un couple ordonné d'items pour chacune ;
- $n(n-1)/2$ extensions d'itemset, une paire d'items distincts pour chacune.

Soit au total $n^2 + n(n-1)/2$ candidats de longueur 2. Pour les 8 items de la base :

$$8 \times 8 + 8 \times \frac{7}{2} = 92$$

La propriété d'anti-monotonie écarte tous les candidats bâtis sur un item non fréquent et ne laisse que les 51 candidats construits sur les 6 items fréquents, soit une élimination de 44,57 % des candidats :

$$1 - \frac{51}{92} \approx 0{,}4457$$

Le même décompte pour 1000 séquences fréquentes de longueur 1 donne :

$$1000 \times 1000 + 1000 \times \frac{999}{2} = 1\,499\,500$$

# Remarque

Le décompte des candidats s'écrit souvent sous la forme d'un produit, $1000 \times 1000 \times (1000 \times 999)/2$ ; cette écriture ne redonne pas $1\,499\,500$, la forme correcte étant $1000 \times 1000 + 1000 \times 999/2$. Le nombre de candidats croît ainsi quadratiquement avec celui des motifs fréquents du niveau précédent, ce qui est l'une des [[Limites des approches générer et élaguer|limites des approches générer puis élaguer]].

Les parenthèses des singletons sont parfois omises : $\langle ab\rangle$ note alors la suite de deux éléments $\langle(a)(b)\rangle$, et non l'itemset $\{a, b\}$, qui s'écrit $\langle(ab)\rangle$ ; la notation parenthésée lève cette ambiguïté.

L'étape la plus coûteuse de l'algorithme est le calcul du support des candidats, et non leur génération : chaque niveau de candidats exige un parcours complet de la base. Les candidats sont conservés en mémoire principale ; il importe donc de limiter les accès au disque, en chargeant la [[Base de séquences|base de séquences]] en mémoire lorsque sa taille le permet.

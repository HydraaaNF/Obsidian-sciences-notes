# Définition

Soient $E$ et $F$ des ensembles finis. L'ensemble des applications de $E$ dans $F$ est noté $\mathcal{A}(E,F)$ ; il est aussi noté $F^E$.

# Propriétés

Soient $E = \{x_1, \dots, x_n\}$ un ensemble à $n$ éléments et $F = \{y_1, \dots, y_p\}$ un ensemble à $p$ éléments. Se donner une application $f$ de $E$ dans $F$ revient à se donner l'image de chacun des éléments de $E$. Or, il y a

- $p$ choix pour $f(x_1)$, puisque $f(x_1)$ peut être égal à $y_1$, ou à $y_2$, ..., ou à $y_p$ ;
- $p$ choix pour $f(x_2)$, puisque $f(x_2)$ peut lui aussi être égal à $y_1$, ou à $y_2$, ..., ou à $y_p$ ;
- et ainsi de suite, jusqu'à $p$ choix pour $f(x_n)$, puisque $f(x_n)$ peut lui aussi être égal à $y_1$, ou à $y_2$, ..., ou à $y_p$.

Il existe donc $p \times p \times \dots \times p = p^n$ applications de $E$ dans $F$.

Soient $E$ et $F$ des ensembles finis. Le nombre d'applications de $E$ dans $F$ est

$$\operatorname{card}(\mathcal{A}(E,F)) = \operatorname{card}(F)^{\operatorname{card}(E)}.$$

**Applications injectives.** Supposons que $n \leq p$, de sorte qu'il existe des applications de $E$ dans $F$ *injectives*. Pour une application injective $f : E \rightarrow F$, le $n$-uplet $(f(x_1), \dots, f(x_n))$ est un [[Arrangement|arrangement]], car les $f(x_i)$ sont tous distincts : chaque $y_i \in F$ a soit 0, soit 1 antécédent dans $E$. Réciproquement, tout arrangement $(y_1, \dots, y_n)$ de $n$ éléments de $F$ définit une application injective de $E$ dans $F$ (l'application $f$ définie par $f(x_i) = y_i$ pour $1 \leq i \leq n$). Ainsi, le nombre d'applications injectives de $E$ dans $F$ est

$$A_p^n = \frac{p!}{(p-n)!}.$$

**Applications bijectives.** En particulier, si $p = n$, le nombre de bijections de $E$ vers $F$ est $n!$ : on retrouve le nombre de [[Permutation|permutations]] de $E$, puisque $F$ a même cardinal que $E$.

**Applications surjectives.** Si $n \geq p$, il existe des applications de $E$ sur $F$ *surjectives*. Leur comptage est bien plus compliqué et n'est pas détaillé.

# Remarque

- La notation $A_p^n$ pour le nombre d'applications injectives suit la convention de l'[[Arrangement]] : on choisit $n$ éléments distincts (les images) parmi les $p$ éléments de $F$. L'écriture $A_n^p = \frac{p!}{(p-n)!}$ est une confusion d'indices fréquente : $A_n^p$ désigne le nombre d'arrangements de $p$ éléments pris parmi $n$, qui vaut $\frac{n!}{(n-p)!}$ et suppose $p \leq n$.
- L'ensemble $\mathcal{A}(E,F)$ des applications de $E$ dans $F$ est aussi noté $F^E$. Avec cette notation, on retient facilement le nombre d'applications : $\operatorname{card}(F^E) = \operatorname{card}(F)^{\operatorname{card}(E)}$.
- Une application de $E$ dans $F$ est déterminée par le $n$-uplet de ses images : le comptage $p^n$ est celui du [[Cardinal d'un produit cartésien|produit cartésien]] $F^n$.
- Les applications de $E$ dans un ensemble à deux éléments sont au nombre de $2^{\operatorname{card}(E)}$ : une application $f : E \to \{0,1\}$ détermine la partie $\{x \in E \mid f(x) = 1\}$. C'est le point de vue du [[Nombre de parties d'un ensemble]].

# Exemple

On considère $n$ boules et $n$ boîtes (assez grandes pour contenir toutes les boules). Supposons, pour fixer les idées, que les boules soient numérotées. L'expérience aléatoire considérée consiste à choisir au hasard une boîte pour la boule 1, une boîte pour la boule 2, ..., une boîte pour la boule $n$. Quelle est la probabilité que chaque boîte soit occupée ?

Un résultat de l'expérience aléatoire est l'affectation d'une boîte à chacune des $n$ boules. Autrement dit, réaliser cette expérience, c'est choisir une application de l'ensemble $E$ des $n$ boules dans l'ensemble $F$ des $n$ boîtes. L'évènement certain $\Omega$ est donc ici l'ensemble $F^E$ des applications de $E$ dans $F$. Il est fini, donc on le munit de la [[Tribu|tribu]] $\mathcal{P}(\Omega)$. Rien dans l'énoncé n'affirmant le contraire, chaque application est considérée équiprobable : on munit cette tribu de l'[[Loi uniforme discrète|équiprobabilité]] sur $\Omega$.

L'évènement $A =$ « chaque boîte est occupée » apparaît avec cette modélisation comme l'ensemble des **surjections** de $E$ sur $F$ (chaque élément de $F$ possède un antécédent). Puisque $\operatorname{card}(F) = \operatorname{card}(E)$, c'est aussi l'ensemble des bijections de $E$ sur $F$.

D'après la formule du nombre d'applications, $\operatorname{card}(\Omega) = n^n$, et d'après le comptage des bijections ci-dessus, $\operatorname{card}(A) = n!$. Finalement,

$$\mathbb{P}(A) = \frac{n!}{n^n} = \frac{(n-1)!}{n^{n-1}}.$$

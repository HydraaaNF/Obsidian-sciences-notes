# Définition

Soient $n$ et $p$ des entiers tels que $1 \leq p \leq n$ et $E$ un ensemble à $n$ éléments. On appelle **arrangement** de $p$ éléments de $E$ toute suite ordonnée $(a_1, \dots, a_p)$ d'éléments de $E$ **tous distincts**. On dit aussi que $(a_1, \dots, a_p)$ est un arrangement de $p$ éléments pris parmi $n$.

On note $A_n^p$ le nombre d'arrangements de $p$ éléments pris parmi $n$, c'est-à-dire le nombre de suites ordonnées de $p$ éléments choisis parmi $n$ éléments possibles avec la contrainte qu'ils soient tous distincts.

# Propriétés

Soient $n$ et $p$ des entiers tels que $1 \leq p \leq n$. Le nombre d'arrangements de $p$ éléments pris parmi $n$ est :

$$A_n^p = n(n-1) \cdots (n-p+1) = \frac{n!}{(n-p)!}.$$

### Démonstration

Pour construire un arrangement $(a_1, \dots, a_p)$ :

- il y a $n$ choix pour $a_1$ ;
- $n-1$ choix pour $a_2$, puisque $a_2$ doit être différent de $a_1$ ;
- $n-2$ choix pour $a_3$, puisque $a_3$ doit être différent de $a_1$ et de $a_2$ ;
- et ainsi de suite ;
- enfin $n-(p-1) = n-p+1$ choix pour $a_p$, puisque $a_p$ doit être distinct de $a_1, \dots, a_{p-1}$.

Il y a donc $n(n-1)(n-2)\dots(n-p+1)$ arrangements.

# Exemple

Une urne contient $2n$ boules numérotées de 1 à $2n$ et on en extrait $2p$ **sans remise** (on suppose $1 \leq p \leq n$). Quelle est la probabilité de tirer alternativement une boule de numéro impair et une boule de numéro pair, en commençant par un numéro impair ?

Un résultat de l'expérience aléatoire est une suite ordonnée $(x_1, \dots, x_{2p})$ d'éléments pris parmi $\{1, \dots, 2n\}$, **tous distincts** puisque le tirage a lieu sans remise. Autrement dit, $\Omega$ est l'ensemble des arrangements de $2p$ éléments de $\{1, \dots, 2n\}$. On le munit de $\mathcal{P}(\Omega)$ et de l'[[Loi uniforme discrète|équiprobabilité]] $\mathbb{P}$ sur $\Omega$.

L'évènement $A$ « tirer alternativement une boule de numéro impair et une boule de numéro pair, en commençant par un numéro impair » est la partie de $\Omega$ formée des suites dont les termes d'indice impair appartiennent à $\{1, 3, \dots, 2n-1\}$ et les termes d'indice pair à $\{2, 4, \dots, 2n\}$ :

$$A = \{(x_1, \dots, x_{2p}) ; \forall i \in \{1, \dots, p\} \ x_{2i-1} \in \{1, 3, \dots, 2n-1\}, \forall i \in \{1, \dots, p\} \ x_{2i} \in \{2, 4, \dots, 2n\}\}.$$

Puisque $\mathbb{P}$ est l'équiprobabilité, $\mathbb{P}(A) = \operatorname{Card}(A)/\operatorname{Card}(\Omega)$. Pour calculer $\operatorname{Card}(A)$, on remarque qu'il y a $n$ choix pour $x_1$ (les $n$ nombres impairs), puis $n$ choix pour $x_2$ (les $n$ nombres pairs), puis $n-1$ choix pour $x_3$ (les nombres impairs distincts de $x_1$), puis $n-1$ choix pour $x_4$ (les nombres pairs distincts de $x_2$), etc., jusqu'à $n-(p-1)$ choix pour $x_{2p-1}$ et $x_{2p}$. Ainsi :

$$\operatorname{Card}(A) = n \cdot n \cdot (n-1) \cdot (n-1) \cdots (n-p+1) \cdot (n-p+1) = \frac{(n!)^2}{((n-p)!)^2}.$$

Comme $\operatorname{Card}(\Omega) = A_{2n}^{2p}$, on obtient finalement :

$$\mathbb{P}(A) = \frac{\operatorname{Card}(A)}{\operatorname{Card}(\Omega)} = \frac{(n!)^2}{((n-p)!)^2}\frac{(2n-2p)!}{(2n)!}.$$

# Remarque

- Dans l'écriture de la partie $A$, l'indice $i$ parcourt $\{1, \dots, p\}$ pour les termes d'indice impair comme pour les termes d'indice pair : les suites considérées ont $2p$ éléments, de sorte qu'il n'existe pas de terme $x_{2i}$ pour $i > p$. L'écriture $\forall i \in \{1, \dots, n\}$ pour la seconde famille d'indices est une erreur fréquente.
- Une suite ordonnée de $p$ éléments de $E$ avec répétitions possibles n'est pas un arrangement : l'arrangement impose que les éléments soient tous distincts : le dénombrement des suites avec répétitions relève du [[Cardinal d'un produit cartésien]].
- Le cas particulier $p = n$ correspond aux [[Permutation|permutations]] de $E$ : une permutation $\sigma$ est connue dès que l'on connaît la suite $(\sigma(x_1), \dots, \sigma(x_n))$, qui est un arrangement des $n$ éléments de $E$.
- Lorsque l'ordre des éléments n'intervient pas, la notion correspondante est la [[Combinaison]].

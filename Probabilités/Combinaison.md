# Définition

Soient $n \in \mathbb{N}$, $E$ un ensemble à $n$ éléments et $p \in \{0, \dots, n\}$. On appelle **combinaison** de $p$ éléments pris parmi les $n$ éléments de $E$ toute partie $\{a_1, \dots, a_p\}$ de $E$.

On note $\binom{n}{p}$ le nombre de combinaisons de $p$ éléments pris parmi $n$ (cela se lit « $p$ parmi $n$ ») : c'est le nombre de parties de $p$ éléments d'un ensemble à $n$ éléments.

# Propriétés

À une combinaison de $p$ éléments correspondent $p!$ arrangements ; en notant $A_n^p$ le nombre d'[[Arrangement|arrangements]] de $p$ éléments pris parmi $n$, on obtient la relation :

$$A_n^p = p! \binom{n}{p}$$

Le nombre de combinaisons de $p$ éléments pris parmi $n$ est :

$$\binom{n}{p} = \frac{n!}{p!(n-p)!}$$

# Remarque

- Les éléments $a_1, \dots, a_p$ d'une combinaison sont **tous distincts**, puisque $\{a_1, \dots, a_p\}$ est un sous-ensemble de $E$.
- De façon simpliste, on peut dire que pour compter les arrangements, « l'ordre intervient », alors que pour compter les combinaisons, « l'ordre n'intervient pas ».
- L'ancienne notation pour $\binom{n}{p}$ est $C_n^p$ ; on la rencontre encore fréquemment.
- Les nombres $\binom{n}{p}$ interviennent dans la [[Formule du binôme de Newton]].

# Exemple

Quand on décrit un ensemble par ses éléments, l'ordre dans lequel on énumère les éléments n'a aucune importance. Par exemple, dans $E = \{1, 2, 3, 4\}$, $\{1, 3, 4\}$ est une combinaison de 3 éléments de $E$, que l'on pourrait tout aussi bien noter $\{4, 1, 3\}$. C'est la différence entre un [[Arrangement|arrangement]] et une combinaison : à une combinaison $\{a_1, \dots, a_p\}$ correspondent $p!$ arrangements, à savoir tous les arrangements que l'on obtient en effectuant des [[Permutation|permutations]] de $a_1, \dots, a_p$. Dans l'exemple précédent, à la combinaison $\{1, 3, 4\}$ correspondent les $3! = 6$ arrangements $(1, 3, 4)$, $(1, 4, 3)$, $(3, 1, 4)$, $(3, 4, 1)$, $(4, 1, 3)$, $(4, 3, 1)$.

Quelle est la probabilité qu'un groupe de 13 cartes extrait au hasard d'un jeu de 52 cartes contienne exactement un as ? au moins un as ?

Prenons pour $\Omega$ l'ensemble des « mains » de 13 cartes prises parmi 52. Toutes les mains étant équiprobables, on complète la modélisation de cette expérience aléatoire en choisissant la [[Tribu|tribu]] $\mathcal{P}(\Omega)$ et l'[[Loi uniforme discrète|équiprobabilité]] sur $\Omega$, notée $\mathbb{P}$ par la suite. On a donc $\mathbb{P}(E) = \frac{\text{card } E}{\text{card } \Omega}$ pour tout $E \in \mathcal{P}(\Omega)$.

Notons $C$ l'ensemble des 52 cartes (évidemment distinctes) et $A$ l'ensemble des 4 as (distincts). L'évènement $F =$ « la main de 13 cartes comporte exactement un as » s'écrit :

$$F = \left\{\{x_1, \dots, x_{13}\} ; x_1 \in A,\ \forall i \in \{2, \dots, 13\} \ x_i \in C \setminus A,\ x_1, \dots, x_{13} \text{ tous distincts}\right\}$$

On a bien $F \subset \Omega$ : $F$ est un [[Évènement]] de l'[[Espace probabilisé|espace probabilisé]] $(\Omega, \mathcal{P}(\Omega), \mathbb{P})$, c'est-à-dire un élément de la tribu $\mathcal{P}(\Omega)$, et la modélisation est valide. Remarquer qu'un élément $\{x_1, \dots, x_{13}\}$ de $F$ est noté avec des accolades et non des parenthèses, car une « main » est un ensemble de 13 cartes, que l'on peut énumérer dans un ordre quelconque mais qui sont toutes distinctes.

Reste à calculer la probabilité de $F$, ce qui revient à calculer son cardinal (le nombre de cas favorables) et le cardinal de $\Omega$ (le nombre de cas possibles). Par définition du nombre de combinaisons de $p$ éléments pris parmi $n$, on a $\text{card } \Omega = \binom{52}{13}$.

Pour définir un élément de $F$, on choisit d'abord $x_1$ parmi les 4 éléments de $A$, ce qui peut se faire de $\binom{4}{1} = 4$ façons, puis on choisit un ensemble de 12 cartes $\{x_2, \dots, x_{13}\}$ parmi les $52 - 4 = 48$ cartes qui ne sont pas des as, ce qui peut se faire de $\binom{48}{12}$ façons. Les deux choix successifs portant sur deux ensembles disjoints (l'ensemble des as et l'ensemble des cartes qui ne sont pas des as), on a $\text{card } F = 4 \times \binom{48}{12}$, puis :

$$\mathbb{P}(F) = \frac{4 \times \binom{48}{12}}{\binom{52}{13}} = \frac{4 \frac{48!}{12!36!}}{\frac{52!}{13!39!}} = 4 \frac{48!13!39!}{52!12!36!} = \frac{4 \cdot 13 \cdot 39 \cdot 38 \cdot 37}{52 \cdot 51 \cdot 50 \cdot 49}$$

Notons maintenant $G =$ « la main de 13 cartes comporte au moins un as ». $G$ est bien un évènement et l'on a $G \subset \Omega$ ; on peut l'écrire :

$$G = \left\{\{x_1, \dots, x_{13}\} ; \forall i \in \{1, \dots, 13\} \ x_i \in C,\ \exists i \in \{1, 2, 3, 4\} \ x_i \in A,\ x_1, \dots, x_{13} \text{ tous distincts}\right\}$$

Deux méthodes permettent de calculer $\mathbb{P}(G)$.

**Première méthode.** Notons $F_i$ l'évènement « la main comporte $i$ as exactement », de sorte que l'évènement $F$ précédent est $F_1$ et que $G = \bigcup_{i=1}^{4} F_i$, l'union étant disjointe. On a donc $\mathbb{P}(G) = \sum_{i=1}^{4} \mathbb{P}(F_i)$, chaque $\mathbb{P}(F_i)$ se calculant par le raisonnement précédent :

$$\mathbb{P}(F_i) = \frac{\text{card } F_i}{\binom{52}{13}}$$

$$\text{avec } \text{card } F_i = \binom{4}{i}\binom{48}{13-i}$$

(choisir d'abord $i$ as parmi 4, puis choisir $13-i$ cartes parmi les 48 qui ne sont pas des as).

**Deuxième méthode** (bien plus rapide). L'évènement $G$ est le complémentaire de l'évènement « la main ne comporte pas d'as », dont le cardinal est $\binom{48}{13}$ (choisir 13 cartes parmi les 48 qui ne sont pas des as). On a donc :

$$\mathbb{P}(G) = 1 - \frac{\binom{48}{13}}{\binom{52}{13}}$$

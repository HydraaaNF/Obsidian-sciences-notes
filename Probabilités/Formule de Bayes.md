# Théorème

La **formule de Bayes** exprime la [[Probabilité conditionnelle|probabilité conditionnelle]] de $B$ sachant $A$ à partir de celle de $A$ sachant $B$ :

$$\mathbb{P}[B \mid A] = \frac{\mathbb{P}[A \mid B]\mathbb{P}[B]}{\mathbb{P}[A]}$$

Si $B_1, \dots, B_n$ forment un [[Système complet d'évènements|système complet d'évènements]] (mutuellement exclusifs et exhaustifs), la formule prend, pour chaque $j$, la forme

$$\begin{aligned} \mathbb{P}[B_j \mid A] &= \frac{\mathbb{P}[B_j \cap A]}{\mathbb{P}[A]} \\ &= \frac{\mathbb{P}[A \mid B_j]\mathbb{P}[B_j]}{\sum_i \mathbb{P}[A \mid B_i]\mathbb{P}[B_i]} \end{aligned}$$

La dernière égalité utilise la [[Probabilités composées|règle de multiplication]] $\mathbb{P}[B_j \cap A] = \mathbb{P}[A \mid B_j]\mathbb{P}[B_j]$.

# Interprétation

La formule inverse le sens du conditionnement : elle donne la probabilité de $B_j$ sachant $A$ à partir des probabilités conditionnelles $\mathbb{P}[A \mid B_i]$ et des probabilités $\mathbb{P}[B_i]$. Le dénominateur $\mathbb{P}[A]$ se calcule à l'aide de la [[Formule des probabilités totales|formule des probabilités totales]].

# Exemple

Trois machines $M_1$, $M_2$ et $M_3$ produisent des boulons. La machine $M_1$ produit en moyenne 0,3 % de boulons défectueux, la machine $M_2$ 0,8 % et la machine $M_3$ 15 %. On mélange 1000 boulons dans un sac, 500 provenant de $M_1$, 350 de $M_2$ et 150 de $M_3$. On tire au hasard un boulon du sac : il est défectueux ! Quelle est la probabilité qu'il ait été produit par $M_1$ ?

On note $D$ l'[[Évènement|évènement]] « le boulon est défectueux ». Les probabilités des machines et les probabilités conditionnelles de défectuosité sont :

- $\mathbb{P}[M_1] = 0{,}5$ ;
- $\mathbb{P}[M_2] = 0{,}35$ ;
- $\mathbb{P}[M_3] = 0{,}15$ ;
- $\mathbb{P}[D \mid M_1] = 0{,}003$ ;
- $\mathbb{P}[D \mid M_2] = 0{,}008$ ;
- $\mathbb{P}[D \mid M_3] = 0{,}15$.

D'après la formule de Bayes,

$$\mathbb{P}[M_1 \mid D] = \frac{\mathbb{P}[D \mid M_1]\mathbb{P}[M_1]}{\mathbb{P}[D \mid M_1]\mathbb{P}[M_1] + \mathbb{P}[D \mid M_2]\mathbb{P}[M_2] + \mathbb{P}[D \mid M_3]\mathbb{P}[M_3]} \approx 5{,}6\%$$

Les probabilités conjointes correspondantes valent

- $\mathbb{P}[M_1 \cap D] = 0{,}0015$ ;
- $\mathbb{P}[M_2 \cap D] = 0{,}0028$ ;
- $\mathbb{P}[M_3 \cap D] = 0{,}0225$.

# Remarque

La proportion de boulons défectueux de la machine $M_3$ est de 15 %, et non de 1 % : la valeur $\mathbb{P}[D \mid M_3] = 0{,}15$ figure dans les données et elle seule redonne les probabilités conjointes ci-dessus et le résultat $\mathbb{P}[M_1 \mid D] \approx 5{,}6\%$.

Au dénominateur de la seconde forme figure le facteur $\mathbb{P}[B_i]$ sous la somme : $\sum_i \mathbb{P}[A \mid B_i]\mathbb{P}[B_i]$, qui n'est autre que $\mathbb{P}[A]$ d'après la [[Formule des probabilités totales|formule des probabilités totales]]. L'écriture $\sum_i \mathbb{P}[A \mid B_i]$, où ce facteur est omis, est une erreur fréquente : elle ne redonne pas la probabilité totale $\mathbb{P}[A]$.

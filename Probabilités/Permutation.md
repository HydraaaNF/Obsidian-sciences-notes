# Définition

Soit $E$ un ensemble. On appelle **permutation** de $E$ toute bijection de $E$ sur lui-même. L'ensemble des permutations de $E$ est noté $\mathcal{S}(E)$.

Lorsque $E$ possède $n$ éléments notés $x_1, \dots, x_n$, se donner une permutation $\sigma$ de $E$, c'est se donner la suite ordonnée des images des $x_i$ : $\sigma$ est connue dès que l'on connaît $(\sigma(x_1), \dots, \sigma(x_n))$.

# Propriétés

Soit $E$ un ensemble à $n$ éléments. Alors

$$\operatorname{Card}\left(\mathcal{S}(E)\right) = n!,$$

*c'est-à-dire* qu'il existe $n!$ permutations de $E$.

### Démonstration

Soit $\sigma$ une permutation de $E$. Comme $\sigma$ est bijective, les images $\sigma(x_i)$ sont toutes distinctes : la suite $(\sigma(x_1), \dots, \sigma(x_n))$ est un arrangement des $n$ éléments de $E$ (voir [[Arrangement]]). Il existe donc $A_n^n$ permutations de $E$. Or $A_n^n = n(n-1) \cdots 1 = n!$, d'où

$$\operatorname{Card}\left(\mathcal{S}(E)\right) = n!.$$

# Exemple

Le mot de passe de Pierre fait 9 caractères, tous distincts, dont le caractère &. Pierre indique à Delphine quels sont ces 9 caractères, et lui dit de plus que & n'est pas en première position. Si Delphine essaie un mot de passe au hasard, quelle est la probabilité qu'elle tombe sur le bon ?

On identifie l'ensemble $E$ des 9 caractères à $\{1, \dots, 9\}$, le caractère & étant codé par $9$. L'univers $\Omega$ est alors l'ensemble des permutations de $E$ dont l'image de $1$ n'est pas $9$ :

$$\Omega = \{\sigma \in \mathcal{S}(\{1, \dots, 9\}) ; \sigma(1) \neq 9\}$$

On munit l'ensemble fini $\Omega$ de la [[Tribu|tribu]] $\mathcal{P}(\Omega)$, et l'on choisit l'[[Loi uniforme discrète|équiprobabilité]] sur $\Omega$ : chaque mot de passe essayé a la même probabilité d'être le bon. Comme un seul mot de passe est bon, la probabilité que Delphine tombe sur le bon en saisissant au hasard un mot de passe n'ayant pas & en première position est $\frac{1}{\operatorname{Card}(\Omega)}$, avec cette modélisation, l'évènement $A =$ « tomber sur le bon mot de passe » est un [[Évènement|évènement élémentaire]], *i.e.* un singleton.

Pour calculer $\operatorname{Card}(\Omega)$, il suffit de remarquer qu'il y a $8$ choix pour $\sigma(1)$ (les caractères de $1$ à $8$), puis $8$ choix pour $\sigma(2)$ (les caractères de $1$ à $9$ distincts de $\sigma(1)$), puis $7$ choix pour $\sigma(3)$, etc., et enfin un seul choix pour $\sigma(9)$. On obtient ainsi

$$\mathbb{P}(A) = \frac{1}{8 \cdot 8!} = \frac{1}{322560}.$$

# Remarque

- Les permutations de $E$ s'identifient aux arrangements des $n$ éléments de $E$ : une permutation est le cas particulier $p = n$ de l'[[Arrangement]].
- À une [[Combinaison]] de $p$ éléments de $E$ correspondent $p!$ arrangements, à savoir tous ceux obtenus en permutant ses éléments : pour compter les arrangements, l'ordre intervient, alors que pour compter les combinaisons, l'ordre n'intervient pas.

# Définition

Considérons le produit cartésien des ensembles $A_1, A_2, \dots, A_n$ :

$$A_1 \times A_2 \times \cdots \times A_n = \{(a_1, a_2, \dots, a_n) \mid a_1 \in A_1, a_2 \in A_2, \dots, a_n \in A_n\}$$

Ses éléments sont les $n$-uplets $(a_1, \dots, a_n)$ dont chaque coordonnée $a_i$ appartient à l'ensemble $A_i$.

# Propriétés

Soient $A_1, \dots, A_n$ des ensembles finis. On a

$$\operatorname{card}(A_1 \times A_2 \times \cdots \times A_n) = \operatorname{card}(A_1)\operatorname{card}(A_2) \cdots \operatorname{card}(A_n)$$

### Démonstration

Pour définir un $n$-uplet $(a_1, \dots, a_n)$, il y a $\operatorname{card}(A_1)$ choix pour l'élément $a_1$, $\operatorname{card}(A_2)$ choix pour l'élément $a_2$, ..., $\operatorname{card}(A_n)$ choix pour l'élément $a_n$. Le nombre de $n$-uplets est donc le produit de ces nombres de choix.

**Cas particulier.** Le nombre de *suites ordonnées* $(a_1, \dots, a_n)$ d'éléments $a_i$ (non forcément distincts) tous choisis dans un ensemble $B$ à $m$ éléments est

$$\operatorname{card}(B^n) = \left(\operatorname{card}(B)\right)^n = m^n$$

# Exemple

Une urne contient $2n$ boules numérotées de $1$ à $2n$ et on en extrait $2p$ **avec remise** (on suppose $n \geq 1$ et $p \geq 1$). Quelle est la probabilité de tirer alternativement une boule de numéro impair et une boule de numéro pair, en commençant par un numéro impair ?

Un résultat de l'expérience aléatoire est ici une suite ordonnée $(x_1, \dots, x_{2p})$ d'éléments pris parmi $\{1, \dots, 2n\}$, pouvant se répéter puisque le tirage a lieu avec remise. Autrement dit :

$$\Omega = \{1, \dots, 2n\} \times \cdots \times \{1, \dots, 2n\} = \{1, \dots, 2n\}^{2p}$$

Nous munissons $\Omega$ de la [[Tribu|tribu]] $\mathcal{P}(\Omega)$ (car $\Omega$ est fini) et choisissons l'[[Loi uniforme discrète|équiprobabilité]] sur $\Omega$, notée $\mathbb{P}$ par la suite. Pour valider la modélisation, pour que $A =$ « tirer alternativement une boule de numéro impair et une boule de numéro pair, en commençant par un numéro impair » soit bien un [[Évènement|évènement]], nous devons l'écrire comme un élément de la tribu, c'est-à-dire ici comme une partie de $\Omega$ :

$$A = \{(x_1, \dots, x_{2p}) ; \forall i \in \{1, \dots, p\} \ x_{2i-1} \in \{1, 3, \dots, 2n-1\}, \ \forall i \in \{1, \dots, p\} \ x_{2i} \in \{2, 4, \dots, 2n\}\}$$

Puisque $\mathbb{P}$ est l'équiprobabilité, on a $\mathbb{P}(A) = \dfrac{\operatorname{card}(A)}{\operatorname{card}(\Omega)}$. D'après la formule du cardinal d'un produit cartésien, $\operatorname{card}(\Omega) = (2n)^{2p}$.

Pour compter les éléments de $A$, on remarque qu'il y a $n$ choix pour $x_1$ (les nombres impairs $1, 3, \dots, 2n-1$), puis $n$ choix pour $x_2$ (les nombres pairs $2, 4, \dots, 2n$), puis $n$ choix pour $x_3$, etc., enfin $n$ choix pour $x_{2p}$. Finalement :

$$\operatorname{card}(A) = n^{2p}$$

$$\mathbb{P}(A) = \frac{n^{2p}}{(2n)^{2p}} = \frac{1}{2^{2p}}$$

# Remarque

- Dans l'écriture de la partie $A$, l'indice $i$ parcourt $\{1, \dots, p\}$ pour les termes d'indice impair comme pour les termes d'indice pair : les suites considérées ont $2p$ éléments, de sorte qu'il n'existe pas de terme $x_{2i}$ pour $i > p$. L'écriture $\forall i \in \{1, \dots, n\}$ pour la seconde famille d'indices est une erreur fréquente.
- Les nombres impairs de $\{1, \dots, 2n\}$ sont $1, 3, \dots, 2n-1$, c'est-à-dire les entiers de la forme $2k-1$ pour $k \in \{1, \dots, n\}$. L'énumération $1, 2, \dots, 2n-1$ désigne au contraire des entiers consécutifs, dont un seul sur deux est impair : la confondre avec la liste des nombres impairs est une erreur fréquente.
- Le cas particulier $\operatorname{card}(B^n) = m^n$ est le point de départ du comptage du [[Nombre d'applications entre ensembles finis]] : une suite ordonnée $(a_1, \dots, a_n)$ d'éléments de $B$ s'identifie à une application de $\{1, \dots, n\}$ dans $B$.
- Le dénombrement des suites ordonnées **sans répétition** relève des [[Arrangement|arrangements]] et non du produit cartésien : dans un arrangement, les éléments de la suite sont tous distincts.

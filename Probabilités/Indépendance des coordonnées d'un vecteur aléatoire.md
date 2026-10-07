# Définition

Soit $X = (X_1, \dots, X_n)$ un [[Vecteur aléatoire|vecteur aléatoire]] de $\mathbb{R}^n$. Ses coordonnées $X_1, \dots, X_n$ sont dites [[Indépendance de variables aléatoires|mutuellement indépendantes]] si, pour tout $I \subset \{1, \dots, n\}$ et pour toute famille $(B_i)_{i \in I}$ de [[Tribu borélienne|boréliens]] (ou d'intervalles), on a

$$\mathbb{P}\left(\bigcap_{i \in I} [X_i \in B_i]\right) = \prod_{i \in I} \mathbb{P}(X_i \in B_i)$$

Pour une telle famille finie de variables aléatoires, il suffit de vérifier cette propriété pour $I = \{1, \dots, n\}$ : si cette propriété est vraie pour toute famille $(B_i)_{i \in \{1, \dots, n\}}$ d'intervalles, elle est a fortiori vraie pour toute famille d'intervalles indexée par une partie $I$ de $\{1, \dots, n\}$, comme on le voit en écrivant

$$\bigcap_{i \in I} [X_i \in B_i] = \left( \bigcap_{i \in I} [X_i \in B_i] \right) \cap \left( \bigcap_{i \notin I} [X_i \in \mathbb{R}] \right)$$

Ainsi, si $(X_1, \dots, X_n)$ est un vecteur aléatoire à valeurs dans $\mathbb{R}^n$, ses coordonnées $X_1, \dots, X_n$ sont mutuellement indépendantes si et seulement si, pour toute famille $\{B_1, \dots, B_n\}$ d'intervalles,

$$\mathbb{P}(X_1 \in B_1, \dots, X_n \in B_n) = \mathbb{P}(X_1 \in B_1) \dots \mathbb{P}(X_n \in B_n)$$

Dans le cas discret, il suffit de vérifier la relation ci-dessus avec des $B_i$ réduits à des singletons, en considérant uniquement les valeurs pouvant être prises par les variables aléatoires $X_i$ : pour tout $n$-uplet $(k_1, \dots, k_n) \in X_1(\Omega) \times \dots \times X_n(\Omega)$,

$$\mathbb{P}(X_1 = k_1, \dots, X_n = k_n) = \mathbb{P}(X_1 = k_1) \dots \mathbb{P}(X_n = k_n)$$

# Théorème

**Condition nécessaire et suffisante d'indépendance des coordonnées.** Soit $(X_1, \dots, X_n)$ un vecteur aléatoire à valeurs dans $\mathbb{R}^n$ continu. Ses coordonnées $X_1, \dots, X_n$ sont mutuellement indépendantes si et seulement si

$$f_{(X_1,\ldots,X_n)}(x_1,\ldots,x_n)=f_{X_1}(x_1)\cdots f_{X_n}(x_n)$$

Autrement dit, les coordonnées sont indépendantes si et seulement si la [[Loi d'un vecteur aléatoire|densité conjointe]] est le produit des [[Lois marginales|densités marginales]].

### Démonstration

La démonstration est faite pour un couple $(X, Y)$ de [[Variable aléatoire continue|variables aléatoires réelles continues]], le cas général ($n \geq 2$) se traitant de la même façon. Soient $I$ et $J$ deux intervalles : on a les deux égalités

$$\begin{aligned} \mathbb{P}(X \in I, Y \in J) &= \iint_{I \times J} f_{(X,Y)}(x,y)\,dx\,dy \\ \mathbb{P}(X \in I)\mathbb{P}(Y \in J) &= \int_I f_X(x)\,dx \int_J f_Y(y)\,dy \end{aligned}$$

Si $X$ et $Y$ sont indépendantes, ces deux quantités sont égales. Or la deuxième s'écrit aussi, grâce au théorème de Tonelli :

$$\iint_{I \times J} f_X(x) f_Y(y) \, dx\,dy$$

ce qui montre que $f_X(x)f_Y(y)$ est une densité pour le couple $(X, Y)$, donc que l'on a pour presque tout $(x, y) \in \mathbb{R}^2$

$$f_X(x)f_Y(y) = f_{(X,Y)}(x,y)$$

Réciproquement, si on a cette égalité, alors

$$\begin{aligned} \mathbb{P}(X \in I, Y \in J) &= \iint_{I \times J} f_X(x) f_Y(y)\,dx\,dy \\ &= \int_I f_X(x)\,dx \int_J f_Y(y)\,dy \quad \text{(Tonelli)} \\ &= \mathbb{P}(X \in I)\mathbb{P}(Y \in J) \end{aligned}$$

donc $X$ et $Y$ sont indépendantes.

# Propriétés

**Critère de factorisation.** Soit $(X, Y)$ un couple continu de [[Variable aléatoire réelle|variables aléatoires réelles]]. Pour que $X$ et $Y$ soient indépendantes, il faut et il suffit que la densité conjointe s'écrive sous la forme

$$f_{(X,Y)}(x,y) = g(x)h(y)$$

### Démonstration

Si l'on a cette factorisation, la densité de $X$ est

$$\begin{aligned} f_X(x) &= \int_{\mathbb{R}} g(x)h(y)dy \\ &= g(x) \int_{\mathbb{R}} h(y)dy \\ &= C_1g(x) \end{aligned}$$

De même, la densité de $Y$ s'écrit $f_Y(y) = C_2h(y)$, et on a

$$\begin{aligned} C_1C_2 &= \int_{\mathbb{R}} h(y)dy \int_{\mathbb{R}} g(x)dx \\ &= \iint_{\mathbb{R}^2} g(x)h(y)dxdy \\ &= \iint_{\mathbb{R}^2} f_{(X,Y)}(x,y)dxdy \\ &= 1 \end{aligned}$$

de sorte que l'on a bien $f_{X,Y}(x,y) = f_X(x)f_Y(y)$, c'est-à-dire l'indépendance de $X$ et de $Y$.

Réciproquement, si $X$ et $Y$ sont indépendantes, alors la densité conjointe est bien de la forme $g(x)h(y)$ puisqu'elle est alors le produit des densités marginales.

# Exemple

**Densité produit de deux exponentielles.** Soit $(X, Y)$ un couple de variables aléatoires réelles admettant une densité de la forme

$$f_{(X,Y)}(x,y) = Ce^{-2x-3y}\mathbf{1}_{\mathbb{R}^+\times\mathbb{R}^+}(x,y)$$

Alors on peut affirmer sans calcul que $X$ et $Y$ sont indépendantes, et que $X$ et $Y$ suivent des [[Loi exponentielle|lois exponentielles]] de paramètres respectifs $2$ et $3$ ($X \sim \mathcal{E}(2)$, $Y \sim \mathcal{E}(3)$). En effet on a

$$\mathbf{1}_{\mathbb{R}^+ \times \mathbb{R}^+}(x, y) = \mathbf{1}_{\mathbb{R}^+}(x)\mathbf{1}_{\mathbb{R}^+}(y)$$

de sorte que la densité conjointe s'écrit bien comme le produit d'une fonction de $x$ et d'une fonction de $y$, qui sont respectivement les densités de $X$ et de $Y$ à une constante multiplicative près. On en déduit que $C$ est le produit des deux constantes de normalisation, c'est-à-dire $C = 2 \times 3 = 6$.

**Couple uniforme sur un disque.** Soit $(X, Y)$ un couple aléatoire de [[Loi uniforme sur un domaine|loi uniforme sur le disque]] $D_R$ de centre $(0, 0)$ et de rayon $R$. La densité conjointe $f_{(X,Y)}(x, y) = \frac{1}{\pi R^2} \mathbf{1}_{D_R}(x, y)$ n'est pas le produit des densités marginales, donc $X$ et $Y$ ne sont pas indépendantes (ce qui est géométriquement clair). Le critère de factorisation permet de conclure même si on n'a pas calculé les densités marginales, puisqu'il est manifestement impossible de décomposer $f_{(X,Y)}(x, y)$ en produit d'une fonction de $x$ et d'une fonction de $y$.

# Remarque

Lorsque la densité conjointe se factorise sous cette forme, la densité de $X$ (respectivement de $Y$) est tout simplement $g(x)$ (respectivement $h(y)$) à une constante multiplicative près. Cela permet de déterminer les [[Lois marginales|lois marginales]] sans aucun calcul, mis à part celui d'une constante de normalisation. Plus généralement, ce critère est vrai pour un $n$-uplet de variables aléatoires réelles avec $n \geq 2$.

L'indicatrice d'un ensemble $A$ se note $\mathbf{1}_A$ et s'évalue en un point : la forme correcte est $\mathbf{1}_{\mathbb{R}^+}(x)$. L'écriture $\mathbf{1}_{\mathbb{R}^+(x)}$ est une erreur fréquente : les accolades de l'indice sont mal fermées, la variable $x$ est absorbée dans l'indice au lieu d'être l'argument de la fonction.

Voir aussi le cas d'un [[Indépendance des coordonnées d'un vecteur gaussien|vecteur gaussien]], dont l'indépendance des coordonnées relève d'un critère spécifique.

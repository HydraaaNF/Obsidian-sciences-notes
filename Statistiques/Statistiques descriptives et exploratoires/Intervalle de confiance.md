# Définition

On dispose d'un [[Échantillon et échantillonnage|échantillon]] $(x_1, \dots, x_n)$ issu de la loi de $X$ et d'un paramètre inconnu $\theta$ à estimer à partir de cet échantillon. Il est souvent plus réaliste de fournir un renseignement du type

$$a \leq \theta \leq b ,$$

plutôt qu'une estimation ponctuelle de la forme $\hat{\theta}(\omega) = c$. Les bornes $a$ et $b$ sont obtenues en fonction de $x_1, \dots, x_n$, et on peut également les noter $a(x_1, \dots, x_n)$ et $b(x_1, \dots, x_n)$. Fournir un tel intervalle $[a, b]$ s'appelle donner une **estimation par intervalle** de $\theta$ ou **estimation ensembliste**.

On introduit ainsi la notion d'**intervalle de confiance** dans lequel $\theta$ se trouve « probablement ». Cependant l'expression

$$\mathbb{P}[a \leq \theta \leq b] = 0,95$$

n'a aucun sens étant donné que $\theta$ est une constante. Pour définir cette notion de façon plus précise, on considère les bornes $a$ et $b$ comme des [[Variable aléatoire|variables aléatoires]]

$$a(X_1, \dots, X_n)$$

$$b(X_1, \dots, X_n)$$

vérifiant

$$\mathbb{P}[a(X_1, \dots, X_n) \leq \theta \leq b(X_1, \dots, X_n)] = 1 - \alpha,$$

et l'intervalle de confiance au *niveau de confiance* $1 - \alpha = 0.95$ issu des observations $x_1, \dots, x_n$ est donné par

$$[a(x_1, \dots, x_n), b(x_1, \dots, x_n)] .$$

Soit $X_1, \dots, X_n$ des variables aléatoires indépendantes et de même loi que $X$ et $\theta$ un paramètre de la loi de $X$. Soit $\alpha \in ]0, 1[$. On suppose que l'on connaît deux variables aléatoires $a(X_1, \dots, X_n)$ et $b(X_1, \dots, X_n)$ telles que

$$\mathbb{P}\left[a(X_1,\ldots,X_n) \leq \theta \leq b(X_1,\ldots,X_n)\right] = 1 - \alpha.$$

Soit $(x_1, \dots, x_n)$ un échantillon issu de la loi de $X$. Alors l'intervalle

$$[a(x_1, \dots, x_n), b(x_1, \dots, x_n)]$$

est appelé **intervalle de confiance** pour $\theta$ de niveau $1-\alpha$ construit à partir de l'échantillon $(x_1, \dots, x_n)$.

# Interprétation

Les bornes $a(X_1, \dots, X_n)$ et $b(X_1, \dots, X_n)$ sont des variables aléatoires : avant l'observation, c'est donc de l'intervalle aléatoire $[a(X_1, \dots, X_n), b(X_1, \dots, X_n)]$ (et non de $\theta$, qui est une constante) que l'on peut dire qu'il contient $\theta$ avec probabilité $1 - \alpha$. L'intervalle numérique $[a(x_1, \dots, x_n), b(x_1, \dots, x_n)]$ obtenu à partir des observations est une réalisation de cet intervalle aléatoire.

La principale difficulté est de déterminer les variables aléatoires $a(X_1, \dots, X_n)$ et $b(X_1, \dots, X_n)$.

Le seuil $\alpha$ est le même paramètre que le [[Risque de première espèce|risque de première espèce]] d'un test statistique. Un cas d'application classique de la méthode est l'[[Intervalle de confiance de la moyenne d'une loi normale de variance connue]].

# Algorithme

Dans tous les cas, il faut partir d'un [[Estimateur|estimateur]] de $\theta$

$$T = f(X_1, \dots, X_n),$$

de préférence le meilleur au vu des informations dont on dispose, et construire les variables aléatoires $a(X_1, \dots, X_n)$ et $b(X_1, \dots, X_n)$ à l'aide de $T$. Pour obtenir un intervalle de confiance de niveau $1 - \alpha$, il faut déterminer la loi d'une fonction de $T$. Plus précisément, la méthode de construction d'un intervalle de confiance de niveau $1 - \alpha$ pour $\theta$ peut se réduire à un programme en quatre points :

1. Introduire un estimateur $T$ de $\theta$, de préférence le meilleur au vu des informations dont on dispose, dont la définition ne comporte pas de paramètre inconnu

$$T = f(X_1, \dots, X_n),$$

2. Construire une variable aléatoire $g(T)$ dépendant de $\theta$, dont on sait déterminer la loi.

3. Déterminer des réels $\lambda$ et $\mu$ tels que

$$\mathbb{P}[\lambda \leq g(T) \leq \mu] = 1 - \alpha.$$

Dans cette équation, $\theta$ apparaît dans l'écriture de l'événement

$$\{\lambda \leq g(T) \leq \mu\}$$

étant donné que la variable aléatoire $g(T)$ dépend de $\theta$.

4. En isolant $\theta$ dans l'expression précédente, on en déduit $a(X_1, \dots, X_n)$ et $b(X_1, \dots, X_n)$ tels que

$$\mathbb{P}\left[(a(X_1,\ldots,X_n) \leq \theta \leq b(X_1,\ldots,X_n))\right] = 1 - \alpha.$$

# Remarque

1. On pourrait également écrire $a(T)$ et $b(T)$ au lieu de $a(X_1, \dots, X_n)$ et $b(X_1, \dots, X_n)$ étant donné qu'ils sont obtenus à partir de $T$, qui lui s'écrit en fonction de $X_1, \dots, X_n$.

2. La troisième étape est grandement facilitée quand la loi de $g(T)$ obtenue à la deuxième étape est tabulée. C'est le cas de la [[Loi gaussienne|loi normale]], de la [[Loi du chi-deux|loi du $\chi^2$]], de la [[Loi de Student]], et même de certaines lois discrètes comme la [[Loi binomiale|loi binômiale]] ou la [[Loi de Poisson|loi de Poisson]]. Si la loi n'est pas tabulée, on est amené à calculer des intégrales de densités ou des sommes de probabilités qui peuvent être pénibles à ajuster à $1 - \alpha$.

3. Le seul paramètre inconnu intervenant dans la définition de $g(T)$ doit être $\theta$, sinon on ne peut pas obtenir les valeurs numériques de $a$ et $b$ en fonction de l'observation $(x_1, \dots, x_n)$ puisqu'il reste une ou plusieurs inconnues « dans » $a$ et/ou $b$.

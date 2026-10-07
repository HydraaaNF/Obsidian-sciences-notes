# Propriétés

Le calcul pratique de l'[[Espérance d'une variable aléatoire|espérance]] s'effectue différemment selon la nature de la variable aléatoire.

**Cas d'une variable aléatoire discrète.** Si $X$ est une [[Variable aléatoire discrète|variable aléatoire discrète]], de [[Loi d'une variable aléatoire|loi de probabilité]] $p_X$, on a

$$\mathbb{E}(X) = \sum_{k \in X(\Omega)} k \, p_X(\{k\}) = \sum_{k \in X(\Omega)} k \, \mathbb{P}(X = k)$$

sous réserve d'existence, c'est-à-dire si et seulement si

$$\sum_{k \in X(\Omega)} |k| \, p_X(\{k\}) < +\infty$$

**Cas d'une variable aléatoire continue.** Si $X$ est une [[Variable aléatoire continue|variable aléatoire continue]], de densité $f_X$, l'intégrale par rapport à $p_X$ n'est plus une somme, mais une « vraie » intégrale (au sens de Lebesgue), par rapport à la mesure $f_X(x)\,\mathrm{d}x$. Autrement dit, dans ce cas,

$$\mathrm{d}p_X(x) = f_X(x)\,\mathrm{d}x$$

On a donc, si $X$ admet une densité,

$$\mathbb{E}(X) = \int_{\mathbb{R}} x \, f_X(x) \, \mathrm{d}x$$

sous réserve d'existence, c'est-à-dire si et seulement si

$$\int_{\mathbb{R}} |x| \, f_X(x) \, \mathrm{d}x < +\infty$$

# Exemple

**Temps d'attente à l'accueil.** Pour comprendre comment calculer l'espérance d'une variable aléatoire qui n'est ni discrète, ni continue, considérons l'exemple du temps d'attente $T$ (en minutes) nécessaire pour joindre un accueil téléphonique.

On suppose que des statistiques ont permis de constater que la personne chargée de l'accueil est occupée à répondre au téléphone pendant $1/3$ de son temps de travail. On constate par ailleurs que, lorsqu'elle est en ligne, elle y reste pendant une durée [[Loi exponentielle|exponentielle]] de moyenne 30 secondes. Quelle est l'espérance de $T$ ?

On admet qu'il est possible de définir une notion « d'espérance conditionnelle », de telle façon que l'on puisse écrire

$$\mathbb{E}(T) = \mathbb{E}(T \mid A)\mathbb{P}(A) + \mathbb{E}(T \mid \overline{A})\mathbb{P}(\overline{A})$$

où $A$ est l'évènement « accueil occupé », de probabilité $\mathbb{P}(A) = 1/3$. Lorsque l'accueil n'est pas occupé, le temps d'attente est nul, donc $\mathbb{E}(T \mid \overline{A}) = 0$. D'autre part, $\mathbb{E}(T \mid A) = 0,5$ min. On obtient finalement

$$\mathbb{E}(T) = \frac{1}{2}\frac{1}{3} + 0\frac{2}{3} = \frac{1}{6} = 0,1667 \text{ min}$$

Le temps d'attente moyen pour joindre l'accueil est donc de 10 secondes.

# Remarque

Plus généralement, ce procédé de calcul de l'espérance d'une variable aléatoire « mixte » est possible dès lors que la variable aléatoire considérée possède « une partie continue » et « une partie discrète » : on est alors ramené à deux calculs d'espérances conditionnelles, l'un correspondant à une loi discrète (donc se faisant via une somme), l'autre correspondant à une loi continue (se faisant via une intégrale).

Des exemples de calcul d'espérance dans le cas discret sont traités dans [[Espérance d'une variable aléatoire]].

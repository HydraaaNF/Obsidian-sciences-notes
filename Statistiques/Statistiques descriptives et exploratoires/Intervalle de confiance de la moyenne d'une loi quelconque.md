# Algorithme

On souhaite estimer $m = \mathbb{E}[X]$, l'[[Espérance d'une variable aléatoire|espérance]] d'une variable aléatoire mère $X$ de loi quelconque (continue ou discrète), à partir d'un [[Échantillon et échantillonnage|échantillon]] de taille $n$ ; on note $\sigma^2 = \mathbb{V}(X)$ la [[Variance|variance]] de $X$.

Si la taille $n$ de l'échantillon est petite, il faut déterminer la loi exacte de la [[Moyenne empirique|moyenne empirique]] $\overline{X}$ en fonction de $m$ pour en déduire un [[Intervalle de confiance|intervalle de confiance]] pour $m$ : chaque cas nécessite donc une étude particulière.

Par contre, si la taille $n$ de l'échantillon est grande (en pratique $n \geq 100$ suffit dans la majorité des cas), on dispose d'un résultat théorique de convergence, le [[Théorème de la limite centrale|théorème « Central Limit »]], qui permet d'approcher, dans presque tous les cas rencontrés en pratique, la loi de $\overline{X}$ par une [[Loi gaussienne|loi normale]].

1. **Cas $\sigma$ connu.** Si $n$ est grand et $\sigma$ connu, le théorème de la limite centrale permet de choisir l'intervalle [[Intervalle de confiance de la moyenne d'une loi normale de variance connue|du cas gaussien de variance connue]] comme intervalle de confiance au niveau $1 - \alpha$ pour $m = \mathbb{E}[X]$ :

$$\left[ \overline{x} - u_{\frac{\alpha}{2}} \frac{\sigma}{\sqrt{n}}, \overline{x} + u_{\frac{\alpha}{2}} \frac{\sigma}{\sqrt{n}} \right].$$

En effet, si $X$ suit une loi quelconque non gaussienne, la loi de $\overline{X}$ n'est pas la loi $\mathcal{N}\left(m, \frac{\sigma^2}{n}\right)$, mais comme $n$ est grand, on peut tout de même utiliser cette loi comme loi *approchée* de $\overline{X}$ (l'existence de $\sigma$ assure que l'on peut appliquer le [[Théorème de la limite centrale|théorème de la limite centrale]]). On peut donc utiliser la table de la loi $\mathcal{N}(0,1)$ pour le [[Quantile de la loi normale centrée réduite|quantile]] $u_{\frac{\alpha}{2}}$, et le reste du raisonnement est identique au cas gaussien.

2. **Cas $\sigma$ inconnu.** Lorsque $\sigma$ est inconnu, l'intervalle précédent ne peut être calculé numériquement. Le nombre d'observations étant important, le théorème de la limite centrale permet d'approximer la loi de la variable aléatoire $\overline{X}$ par une loi normale. Afin d'utiliser une approche similaire à celle adoptée pour un [[Intervalle de confiance de la moyenne d'une loi normale de variance inconnue|échantillon gaussien de variance inconnue]], il faut disposer de plusieurs réalisations de $\overline{X}$, c'est-à-dire plusieurs observations $\overline{x}_1, \dots, \overline{x}_p$ du phénomène moyen représenté par $\overline{X}$. Cependant, on ne dispose que d'une seule observation de $\overline{X}$, c'est-à-dire $\overline{x}$ : pour avoir d'autres observations issues du phénomène « moyen » qui est gaussien, la pratique est l'utilisation de la [[Méthode du bootstrap|méthode bootstrap]].

Pour appliquer la méthode du bootstrap, il faut donc disposer d'un ordinateur et d'un programme de génération de nombres aléatoires. Si l'on ne dispose que d'un papier et d'un crayon, on peut faire une approximation très grossière de l'intervalle de confiance en procédant de la façon suivante :

1. Comme $n$ est grand, l'estimateur $S'^2$ (la [[Loi de la variance empirique corrigée|variance empirique corrigée]]) est très proche de $\sigma^2$ car il est [[Estimateur fortement convergent|fortement convergent]], et on estime $\sigma$ par $S'$. On peut également l'estimer par $S$, $n$ étant grand, le [[Biais d'un estimateur|biais]] devient négligeable.

2. On considère donc la suite de variables aléatoires

   $$Y_n = \frac{\overline{X} - m}{\frac{S'}{\sqrt{n}}}$$

   et on remarque que

   $$Y_n = Z_n \frac{\sigma}{S'}$$

   où $Z_n$ est la variable aléatoire centrée réduite du [[Théorème de la limite centrale|théorème de la limite centrale]]. Alors, d'une part $Z_n$ [[Convergence en loi|converge en loi]] vers une variable aléatoire $\mathcal{N}(0,1)$ en vertu du théorème de la limite centrale, d'autre part $\frac{\sigma}{S'}$ [[Convergence presque sûre|converge presque sûrement]] vers $1$ en vertu de la [[Loi forte des grands nombres|loi forte des grands nombres]] : les $X_i$ sont i.i.d. avec un moment d'ordre 2, donc les $X_i^2$ sont i.i.d. avec un moment d'ordre 1, d'où

   $$S^2 = \overline{X^2} - \overline{X}^2 \xrightarrow{p.s.} \sigma^2$$

   Ici, $S^2$ est la [[Variance empirique|variance empirique]]. Ainsi, il en résulte que $Y_n$ converge en loi vers $\mathcal{N}(0,1)$.

3. Cela signifie que, pour $n$ grand, on « peut » remplacer $\sigma$ inconnu par son estimation $s'$ (ou par $s$) dans l'intervalle du cas $\sigma$ connu pour obtenir un intervalle de confiance au niveau $1 - \alpha$ pour $m$. Cet intervalle est donc

   $$\left[ \overline{x} - u_{\frac{\alpha}{2}} \frac{s'}{\sqrt{n}}, \overline{x} + u_{\frac{\alpha}{2}} \frac{s'}{\sqrt{n}} \right].$$

# Interprétation

Dans le cas gaussien, la loi de $\overline{X}$ est *exactement* $\mathcal{N}\left(m, \frac{\sigma^2}{n}\right)$. Dans le cas d'une loi *quelconque*, cette loi $\mathcal{N}\left(m, \frac{\sigma^2}{n}\right)$ *approche* la loi exacte de $\overline{X}$ lorsque $n$ est grand. On notera que

$$\mathbb{E}[\overline{X}] = m$$

$$\mathbb{V}(\overline{X}) = \frac{\sigma^2}{n}$$

donc le théorème de la limite centrale précise simplement que l'on peut considérer la loi normale comme « universelle » pour la [[Moyenne empirique|moyenne empirique]] dans le cas de grands échantillons.

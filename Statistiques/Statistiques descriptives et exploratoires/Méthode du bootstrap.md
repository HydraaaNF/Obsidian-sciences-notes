# Définition

La méthode du bootstrap est une méthode de simulation qui fournit plusieurs réalisations $\overline{x}_1, \dots, \overline{x}_p$ de la [[Moyenne empirique|moyenne]] $\overline{X}$ d'un [[Échantillon et échantillonnage|échantillon]], à partir desquelles on construit un [[Intervalle de confiance|intervalle de confiance]] pour la moyenne $m$ à l'aide de la [[Loi de Student|loi de Student]].

# Algorithme

1. À partir des observations $x_1, \dots, x_n$, on obtient un diagramme de fréquences qui est une bonne approximation $\tilde{f}$ de la densité (distribution) de probabilité $f$ de la loi mère.
2. À partir de $\tilde{f}$, on procède à un *re-échantillonnage*, c'est-à-dire que l'on tire aléatoirement $q$ nouvelles observations de ce phénomène à l'aide d'un algorithme de simulation. En calculant la moyenne de ces $q$ tirages de densité mère $\tilde{f}$, on a donc une première réalisation $\overline{x}_1$ de $\overline{X}$. On peut remarquer ici que $\overline{X}$ représente la moyenne d'un échantillon de taille $q$, et on peut approximer sa loi par une [[Loi gaussienne|loi normale]] $\mathcal{N}(m, \sigma^2/q)$.
   En itérant $p$ fois ce processus, on obtient $\overline{x}_1, \dots, \overline{x}_p$ qui sont des réalisations de $\overline{X}$ qui est supposée gaussienne.
3. On dispose à présent des observations $\overline{x}_1, \dots, \overline{x}_p$ d'un phénomène gaussien de moyenne $m$ et de variance inconnue (ici $\sigma^2/q$), on peut donc déterminer un intervalle de confiance pour $m$ à l'aide de la loi de Student.

# Remarque

Pour appliquer la méthode du bootstrap, il faut donc disposer d'un ordinateur et d'un programme de génération de nombres aléatoires. Si l'on ne dispose que d'un papier et d'un crayon, on peut faire une approximation très grossière de l'intervalle de confiance en procédant de la façon suivante :

1. Comme $n$ est grand, l'estimateur $S'^2$ (la [[Loi de la variance empirique corrigée|variance empirique corrigée]]) est très proche de $\sigma^2$ car il est [[Estimateur fortement convergent|fortement convergent]] ; on estime donc $\sigma$ par $S'$. On peut également l'estimer par $S$, $n$ étant grand, le [[Biais d'un estimateur|biais]] devenant négligeable.
2. On considère donc la suite de variables aléatoires

$$Y_n = \frac{\overline{X} - m}{\frac{S'}{\sqrt{n}}}$$

et on remarque que

$$Y_n = Z_n \frac{\sigma}{S'}$$

où $Z_n$ est la variable aléatoire centrée réduite du [[Théorème de la limite centrale|théorème central limite]]. Alors, d'une part $Z_n$ [[Convergence en loi|converge en loi]] vers une variable aléatoire $\mathcal{N}(0,1)$ en vertu du théorème central limite, d'autre part $\frac{\sigma}{S'}$ [[Convergence presque sûre|converge presque sûrement]] vers $1$ en vertu de la [[Loi forte des grands nombres|loi forte des grands nombres]] : les $X_i$ sont i.i.d. avec un moment d'ordre 2, donc les $X_i^2$ sont i.i.d. avec un moment d'ordre 1, d'où

$$S^2 = \overline{X^2} - \overline{X}^2 \xrightarrow{p.s.} \sigma^2$$

Ici, $S^2$ est la [[Variance empirique|variance empirique]]. Ainsi, il en résulte que $Y_n$ converge en loi vers $\mathcal{N}(0,1)$.
3. Cela signifie que pour $n$ grand, on « peut » remplacer $\sigma$, inconnu, par son estimation $s'$ (ou par $s$) dans [[Intervalle de confiance de la moyenne d'une loi quelconque|l'intervalle de confiance de la moyenne]] pour obtenir un intervalle de confiance au niveau $1 - \alpha$ pour $m$. Cet intervalle est donc

$$\left[ \overline{x} - u_{\frac{\alpha}{2}} \frac{s'}{\sqrt{n}}, \overline{x} + u_{\frac{\alpha}{2}} \frac{s'}{\sqrt{n}} \right]$$

où $u_{\frac{\alpha}{2}}$ est le [[Quantile de la loi normale centrée réduite|quantile]] de la loi normale centrée réduite.

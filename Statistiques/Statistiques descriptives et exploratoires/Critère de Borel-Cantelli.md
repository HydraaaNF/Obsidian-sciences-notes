# Théorème

Soit $(X_n)_{n \in \mathbb{N}}$ une suite de [[Variable aléatoire réelle|variables aléatoires réelles]] et $X$ une variable aléatoire réelle, définies sur un même [[Espace probabilisé|espace probabilisé]]. Si, pour tout $\eta > 0$, la **série** de terme général $\mathbb{P}[|X_n - X| > \eta]$ est convergente, alors la suite $(X_n)_{n \in \mathbb{N}}$ converge [[Convergence presque sûre|presque sûrement]] vers $X$.

# Interprétation

Vérifier directement la définition de la [[Convergence presque sûre|convergence presque sûre]] n'est pas aisé en pratique. Le critère de Borel-Cantelli est une condition **suffisante** (admise) pour démontrer une convergence presque sûre : il suffit que la série des probabilités $\mathbb{P}[|X_n - X| > \eta]$ converge pour tout $\eta > 0$.

# Remarque

On a donc toujours intérêt à commencer par calculer $\mathbb{P}[|X_n - X| > \eta]$. Si la **suite** de terme général $\mathbb{P}[|X_n - X| > \eta]$ converge vers 0, il y a [[Convergence en probabilité|convergence en probabilité]] ; si la **série** converge, ce qui est plus fort, il y a convergence presque sûre, donc convergence en probabilité.

La condition de Borel-Cantelli n'est pas une condition nécessaire de convergence presque sûre.

# Exemple

On considère la suite de variables aléatoires réelles $(X_n)_{n \in \mathbb{N}^*}$ où pour tout $n \in \mathbb{N}^*$

$$\mathbb{P}[X_n = a_n] = p_n$$

$$\mathbb{P}[X_n = 0] = 1 - p_n.$$

1. Si la série $\sum p_n$ converge : nécessairement $\lim_{n \to +\infty} p_n = 0$ et $X_n \xrightarrow{\mathbb{P}} 0$. Ainsi, si $(X_n)_{n \in \mathbb{N}^*}$ converge presque sûrement vers une variable aléatoire $X$, alors $X = 0$ presque sûrement. De plus, pour tout $\eta > 0$,

$$\mathbb{P}[|X_n| > \eta] \leq p_n$$

D'après le critère de comparaison de séries à termes positifs, la série de terme général $\mathbb{P}[|X_n| > \eta]$ converge. D'après le critère de Borel-Cantelli, on conclut que $X_n \xrightarrow{p.s.} 0$.

2. Si $\lim_{n \to +\infty} a_n = 0$ : pour tout $\eta > 0$, tous les termes

$$\mathbb{P}[|X_n| > \eta] = 0$$

à partir d'un certain rang. En conséquence, la série $\sum \mathbb{P}[|X_n| > \eta]$ converge. D'après le critère de Borel-Cantelli, on conclut de nouveau que $X_n \xrightarrow{p.s.} 0$.
